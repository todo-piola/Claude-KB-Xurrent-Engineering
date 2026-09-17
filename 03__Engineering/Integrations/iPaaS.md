# Engineering/Integrations/iPaaS.md

Official reference for Xurrent iPaaS Runbook connector actions. This file is the primary source of information for iPaaS questions — consult it before answering from general knowledge. Each action documents its input parameters, output shape, error handling, and best practices as officially specified. Append new actions below following the same structure.

---

## Purpose

Xurrent iPaaS Runbooks orchestrate integration logic as a sequence of connector actions. This file catalogs the officially documented actions available from Xurrent-provided connectors (starting with the Common connector), so that runbook design can rely on verified input/output contracts instead of assumption.

## Action: Send HTTP Request (Common Connector)

Send a custom HTTP request to an external application. Returns the response's status code, headers, and body to the workflow.

**Use case**: send an HTTP request to an internal or external service.

### Input Parameters

| Parameter | Type | Required | Default | Description |
|---|---|---|---|---|
| `method` | Enum | Yes | - | One of `HEAD`, `GET`, `POST`, `PUT`, `PATCH`, `DELETE`, `OPTIONS`, `TRACE` |
| `path` | String | No | - | Sub-path appended to the connection's Base URL (e.g. `/users/1`). Allowed characters match `[A-Za-z0-9\-._~!$&'()*+,;=:@%/]`; put query strings in `query_parameters` — URL fragments (`#...`) are not supported |
| `headers` | Array of `{name, value}` | No | `[]` | Request headers. Header names must match `[A-Za-z0-9\-_]+`. The connector joins repeated names into a single comma-separated value |
| `query_parameters` | Array of `{name, value, already_encoded}` | No | `[]` | Query-string parameters. Names may include `$` for OData system parameters (e.g. Microsoft Graph's `$filter`, `$top`, `$skiptoken`) and `[`/`]` for APIs using `filter[field]`-style keys. Names are percent-encoded on the wire, so `$filter` is sent as `%24filter`. The connector appends `[]` to repeated names: two `q` entries become `q[]=A&q[]=B` on the wire. Set `already_encoded` on an entry whose value is already percent-encoded, such as one lifted from a signed URL, so it is not escaped a second time — see Already-encoded values below |
| `body` | Binary | No | - | Raw request body. The connector does not auto-serialise. Send JSON by setting a `Content-Type: application/json` header and a stringified JSON body |

### Already-encoded values

Set `already_encoded` on an entry whose value is already percent-encoded, typically one lifted out of a signed URL (CloudFront, S3, Azure SAS), whose signature is computed over the literal query string. Existing escapes are then preserved exactly: `%3B` stays `%3B` and `+` stays `+`.

Four things change for the whole request once any entry sets it:

- Parameters are normally sorted by name on the wire. With `already_encoded` in play the query string keeps the order you listed the entries in, which is what signature validation needs. Repeats group at the first entry with that name, so `q=A, x=V, q=B` is sent as `q=A&q=B&x=V`.
- An `already_encoded` entry is never `[]`-expanded, and that applies to its whole group: an entry sharing its name loses the `[]` too.
- A connection whose credential is placed in Query params contributes that parameter first, ahead of the entries you list, so such a connection cannot be combined with a signed URL.
- A parameter grouped with an `already_encoded` entry must be a scalar; a nested object or array there fails the request rather than being sent in a different shape.

An `already_encoded` value is rejected, with a message naming the character and its position, when it contains a bare `&` or `;` (either would split it into further parameters), a tab, carriage return or newline (the URL layer deletes these silently), or a `%` that is not followed by two hex digits. Use `%26`, `%3B`, `%09`, `%0D`, `%0A` or `%25` for one that belongs to the value. A literal space or `#` is still escaped to `%20` or `%23`, since the result has to be a legal URL query.

### Defaults

The connector sends `User-Agent: Xurrent iPaaS` on every request. Override it by adding a `User-Agent` entry to `headers`.

### Example Input

```json
{
  "method": "GET",
  "path": "/users/1",
  "headers": [{ "name": "Accept", "value": "application/json" }],
  "query_parameters": [{ "name": "include", "value": "profile" }],
  "body": null
}
```

### Output

| Field | Type | Required | Description |
|---|---|---|---|
| `response.status` | Integer | Yes | HTTP status code |
| `response.headers` | Array of `{name, value}` | No | One entry per response header name. When the response repeats a header name, the connector combines the values into a single comma-joined value per RFC 9110 §5.3. A header the server sends with an empty field value is returned with an empty string value, not dropped |
| `response.body` | Binary | No | Raw response body |

### Example Output

```json
{
  "response": {
    "status": 200,
    "headers": [
      { "name": "content-type", "value": "application/json" },
      { "name": "x-request-id", "value": "abc-123" }
    ],
    "body": "{\"id\":1,\"name\":\"Ada Lovelace\"}"
  }
}
```

### Error Handling

The connector does not retry or back off. The connector returns any HTTP response to the workflow as-is, including 4xx and 5xx. Handle status codes in your runbook (e.g. branch on `response.status >= 400`). If the connector cannot send the request at all (DNS failure, TLS error, timeout), the action fails with the underlying error.

### Best Practices

- Branch on `response.status >= 400` in the runbook. The connector never retries and never fails on HTTP error responses.
- Send JSON bodies by setting `Content-Type: application/json` in `headers` and passing a stringified JSON body. The connector does not auto-serialise.
- Use one of the four configured auth modes instead of pasting credentials into `headers`, `query_parameters`, or `body`. The platform logs those fields as-is and does not treat them as secrets.
- Prefer a dedicated vendor connector when one exists. HTTP has no pagination helpers, response-body parsing, or rate-limit handling.

[Confirmed] — official connector documentation.

## Action: Evaluate Ruby Code (Common Connector)

Runs a Ruby script with caller-defined input and output schemas. Values assigned to `output[:field]` inside the script are returned under `results`. The script is validated against an allowlist of methods before execution. This action does not execute arbitrary Ruby.

### Common Use Cases

- **Reshape action output**: map `action_output('list_devices')` into a slimmer array of hashes before handing it to the next step.
- **Custom validation**: assert an invariant on upstream data (`fail_job!('no users found')`) so the runbook stops before a destructive action.
- **Derived fields**: select the parts of an action's output that several downstream actions reuse, computing the selection once instead of repeating it in every step, or normalise a timestamp (`1.hour.ago.iso8601`) before handing it on.
- **Secret handling**: call `decrypt_secret_string(input[:token])`, use the plain value in a computed header, and surface the result as a `secret_string` via `make_secret_string(...)`.
- **Human-readable formatting**: `number_to_human_size(bytes)` or `strftime('%Y-%m-%d')` for values rendered in Xurrent records.

### Input Parameters

| Parameter | Type | Required | Default | Description |
|---|---|---|---|---|
| `input_schema` | `SchemaField[]` | No | `[]` | Field definitions for the script's inputs. Each entry has `id`, `label`, `type` (`string`, `integer`, `secret_string`, …), `required` |
| `output_schema` | `SchemaField[]` | No | `[]` | Field definitions for the values returned under `results`. The runtime validates types and required fields after execution |
| `input` | Nested | Conditional | n/a | Values that match `input_schema`. Required when any `input_schema` entry has `required: true` |
| `proc` | Ruby | Yes | n/a | Ruby script to execute. Access inputs via `input[:key]` (or `input['key']`) and return data via `output[:key] = value` |

### Example Input

```json
{
  "input_schema": [
    { "id": "i", "label": "Number", "type": "integer", "required": true },
    { "id": "a", "label": "First string", "type": "string", "required": true },
    { "id": "b", "label": "Second string", "type": "string", "required": true }
  ],
  "output_schema": [
    { "id": "greeting", "label": "Greeting", "type": "string", "required": true }
  ],
  "input": { "i": 4, "a": "hello", "b": "world" },
  "proc": "if input['i'] > 3\n  output['greeting'] = input['a'] + ' moon'\nelse\n  output['greeting'] = 'bye ' + input['b']\nend"
}
```

### Output

| Field Name | Type | Description |
|---|---|---|
| `results` | Nested | Hash populated by the script. See Results object fields below |

#### Results object fields

Fields are defined by `output_schema`. The runtime enforces the declared types and required flags; wrong types or missing required fields raise `IPaaS::Job::FailJob` with `Nested field 'results' invalid: …`.

### Example Output

```json
{
  "results": { "greeting": "hello moon" }
}
```

### Allowed Ruby methods

Every method call in the script is validated against the allowlist before execution. The groups below sample the most frequently used methods per category. For the full authoritative list, see `connector/lib/ipaas/connector/common/proc_rules/valid_methods_rule.rb`.

| Category | Representative methods |
|---|---|
| Base / comparison | `present?`, `blank?`, `nil?`, `presence`, `is_a?`, `tap`, `itself`, `to_json`, `pretty_generate`, `raise`, `Float`, `lambda`, `call`, `==`, `!=`, `<`, `<=`, `>`, `>=`, `!` |
| Strings | `split`, `gsub`, `sub`, `tr`, `strip`, `lstrip`, `rstrip`, `match`, `match?`, `captures`, `start_with?`, `end_with?`, `index`, `reverse`, `downcase`, `upcase`, `capitalize`, `swapcase`, `titleize`, `camelcase`, `underscore`, `strftime`, `to_i`, `to_f`, `to_sym`, `bytesize` |
| Numbers | `+`, `-`, `*`, `/`, `%`, `**`, `to_s`, `to_i`, `to_f`, `abs`, `ceil`, `times`, durations (`seconds`, `minutes`, `hours`, `days`, `weeks`, `fortnights`), byte helpers (`bytes`, `kilobytes`, `megabytes`, `gigabytes`, `terabytes`, …), `number_to_human_size` |
| Hashes | `[]`, `[]=`, `dig`, `drill`, `fetch`, `key?`, `delete`, `except`, `slice`, `merge`, `reduce`, `keys`, `values`, `each_value`, `transform_keys`, `transform_values`, `with_indifferent_access`, `deep_dup`, `to_a` |
| Arrays | `[]`, `<<`, `push`, `length`, `size`, `first`, `last`, `include?`, `exclude?`, `each`, `each_with_index`, `each_with_object`, `each_slice`, `map`, `flat_map`, `filter`, `filter_map`, `select`, `reject`, `detect`, `reduce`, `sum`, `min`, `max`, `sort`, `sort_by`, `group_by`, `index_by`, `pluck`, `pick`, `uniq`, `compact`, `compact_blank`, `flatten`, `zip`, `take`, `to_h`, `to_set`, `any?`, `all?`, `none?` |
| Time | `Time.now`, `Time.current`, `Time.parse`, `utc`, `to_datetime`, `iso8601`, `zone`, `ago`, `at` |
| XML | `text`, `at_xpath` |

Calling anything outside the allowlist (including `eval`, `system`, `exec`, `require`, `instance_eval`, method / constant definitions, direct instance / class / global variables) is rejected at validation time with `Method '<name>' not allowed.`.

### Available iPaaS helpers

In addition to the allowed Ruby methods, the platform provides the helpers below.

**Runbook-native (common)**

| Helper | Purpose |
|---|---|
| `log(message)` | Emit a log line on the runbook run |
| `fail_job!(message)` | Fail the action with a custom message. Prefer this over `raise` |
| `finish_job!(message)` | Early exit: complete the job before the end of the runbook, skipping subsequent actions |
| `backoff(message, retry_after:)` | Signal the runbook runner to wait before continuing |
| `input` | The values mapped into this action's input field, with indifferent access |
| `job_context_identifier`, `job_context_identifier=` | Read / set the run's identifier, facilitates filtering of jobs |

**Secrets**

| Helper | Purpose |
|---|---|
| `decrypt_secret_string(value)` | Decrypt a `secret_string` input into a plain string |
| `make_secret_string(value)`, `new_secret_string(value)` | Wrap a plain value as a secret. Use when writing a `secret_string` output |

**Data & name helpers**

| Helper | Purpose |
|---|---|
| `compact_hash(hash)` | Remove nil / blank values from a hash |
| `camel_to_snake(string)` | Convert camelCase → snake_case |
| `humanize_field_name(string)` | Humanise a schema field name |
| `keys_to_field_id(hash)` | Convert keys to field-id form |
| `detect_content_type` | Detect a response's content type |
| `parse_json_response(body)` | Parse a JSON response body into a hash or array. Fails the job when the body is not valid JSON |
| `parse_xml_response(body)` | Parse an XML response body into a document with namespaces removed. Read values out of it with `at_xpath` and `text` |

**Advanced helpers — available but prefer alternatives**

Reading or updating runbook state from inside the script is possible, but hides dependencies. Prefer mapping values so the wiring is visible in the runbook.

| Helper | Purpose |
|---|---|
| `trigger_output` | Read the runbook's trigger output. Prefer an explicit input field |
| `action_output(ref)` | Read the output of another action in the same runbook, validated against existing references at save time. Prefer an explicit input field |
| `read_variable(name)` | Read a runbook variable. Prefer an explicit input field |
| `write_variable(name, value)` | Write a runbook variable. Prefer the 'Assign Runbook Variable' action |

**Primarily for connector authoring — available but not idiomatic here**

| Helper | Purpose |
|---|---|
| `http_send(method, url, **options)` | Outbound HTTP request |
| `outbound_connection.store.read(key)`, `outbound_connection.store.write(key, value)` | Persistent store shared by every Ruby action step wired to the same Ruby connection |
| `encode_jwt(payload, …)`, `decode_jwt!(token, …)` | JWT encode / decode |
| `make_jwt_payload(…)` | Build a JWT payload |
| `pem_valid?(pem)` | Check PEM validity |
| `runbook` | The running runbook. Exposes `runbook.uuid`, `runbook.account_id` and `runbook.read_variable(name)` |
| `account_id` | Xurrent account the run belongs to |

### Error Handling

Errors surface at three points:

| Stage | Trigger | Message shape |
|---|---|---|
| Script validation (before execution) | Disallowed method call | `Method '<name>' not allowed.` |
| Script validation (before execution) | `action_output('<ref>')` references a step that doesn't exist | `(proc) invalid action references: '<ref>', …` |
| Input validation (before execution) | Input values don't match `input_schema` types / required flags | `Nested field 'input' invalid: Type of field '<x>' invalid, expected <T> found <U>.` |
| Runtime | Any uncaught exception raised inside the script | The exception class and message propagate |
| Runtime | Intentional failure | Call `fail_job!('<reason>')`. Produces a clean error carrying that message |
| Output validation (after execution) | `results` don't match `output_schema` types / required flags | `Output [] invalid: Nested field 'results' invalid: …` |

### Best Practices

- Use the Ruby connector for glue logic only. Reshape data, validate invariants, compute derived fields. Anything that calls an external API belongs in a dedicated connector.
- Declare `input_schema` and `output_schema` up front. The surrounding runbook editor uses them to validate wiring, and the runtime uses them to type-check at the boundaries.
- Return data through `output[:field] = value`. The script's return value is discarded.
- Access inputs via `input[:key]` or `input['key']`. The hash is with_indifferent_access.
- Protect secrets: call `decrypt_secret_string(input[:x])` only as late as needed and never `log(...)` a decrypted value; wrap outgoing secret values with `make_secret_string(value)` when the `output_schema` declares a `secret_string` field.
- Prefer `fail_job!('reason')` over `raise` for unrecoverable conditions. It produces a clean error on the job without a Ruby stack trace.
- When the script needs to pause, call `backoff` and let the runbook runner reschedule the action. `sleep` is not allowed.
- If the validator rejects a method, pick an allowed alternative from the lists above.
- Keep scripts small. For logic that repeats across runbooks, add a dedicated connector action instead of pasting a large script into each runbook.

[Confirmed] — official connector documentation.

## Related entries

- `Engineering/KnownLimitations.md` — "Personal Access Token permission changes do not apply retroactively to the existing token", "CMDB import apps require a resolvable Support Team before creating any CI"
- `Integrations/Webhooks.md` — inbound (Webhook) vs. outbound (iPaaS Runbook) integration mechanisms and shared authentication concerns
- `Platform/AutomationRules.md` — `Call`/`Payload` fields, for triggering a Runbook from an Automation Rule
