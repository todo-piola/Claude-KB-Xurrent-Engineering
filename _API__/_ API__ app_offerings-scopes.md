# App Offerings - Scopes API

- [List all scopes of an app offering](index.html#list-all-scopes-of-an-app-offering)
- [Get a single scope of an app offering](index.html#list-all-scopes-of-an-app-offering)
- [Fields](index.html#fields)

## List all scopes of an app offering

List all scopes of an app offering with a specific ID.

```
GET /app_offerings/:id/scopes
```

### Response

```
status: 200 OK
```

```
[{"id":1,"effect":"allow","actions":["request:Read","request:Update"],"nodeID":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of app offering scopes:

`id` `effect` `actions`

## Get a single scope of an app offering

```
GET /app_offerings/:id/scopes/:scope_id
```

### Response

```
status: 200 OK
```

```
{"id":1,"effect":"allow","actions":["request:Read","request:Update"],"nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Fields

actions
: *Required* **array of [string](../../general/data_types.html)** — Actions this scope applies to. Each action has the format `<record type>:<operation>`.

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the scope was created.

conditions
: *Required* **array of [string](../../general/data_types.html)** — Conditions for this scope.

effect
: *Required* **[enum](../../general/data_types.html)**, default: `allow` — Whether this scope allows or prevents access. Valid values are:
: - `allow`: Allow the actions of this scope
 - `deny`: Deny (i.e. do not allow) the actions of this scope

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the scope.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the scope.
 If the scope has no updates it contains the `created_at` value.
