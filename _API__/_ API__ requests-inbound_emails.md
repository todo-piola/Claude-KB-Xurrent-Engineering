# Requests - Inbound emails API

- [List inbound emails of a request](../inbound_emails.html#list-notes-of-a-request)
- [Fields](../inbound_emails.html#fields)

## List inbound emails of a request

List all inbound emails of a request with a specific ID.

```
GET /requests/:id/inbound_emails
```

### Response

```
status: 200 OK
```

```
[{"id":9,"created_at":"2024-03-14T07:32:38-05:00","message_id":"<xyz>","from":"beatrice.baldwin@widget.com","to":"wdc@xurrent.com","subject":"Upgrade HP OpenView NNM to v10 (NNM10)","body_start":"Our purchase department received a letter from HP announcing the End of Support for ...","source_uri":"https://...","note":{"id":3848,"nodeID":"..."},"failure_reason":null,"nodeID":"..."},"..."]
```

The response contains [these fields](../inbound_emails.html#collection-fields) by default.

### Collection Fields

By default the following [fields](../inbound_emails.html#fields) will appear in collections of inbound emails:

`body_start` `cc` `created_at` `failure_reason` `from` `id` `message_id` `note` `source_uri` `subject` `to`

Obtain a different set of [fields](../inbound_emails.html#fields) using the [?fields= parameter](../../general/field_selection/index.html#collection-of-resources).

### Sorting

The collection of inbound emails is sorted **ascending** by `id`.

The following [fields](../inbound_emails.html#fields) are accepted by the [?sort= parameter](../../general/ordering.html):

`id` `created_at`

## Fields

body\_start
: *Readonly* **[string](../../general/data_types.html)** — The first 255 characters of the body of the inbound email.

cc
: *Readonly* **[string](../../general/data_types.html)** — The value of the CC field of the inbound email.

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the inbound email was received.

failure\_reason
: *Readonly* **[string](../../general/data_types.html)** — When the inbound email did not process successfully, contains the reason why processing failed.

from
: *Readonly* **[string](../../general/data_types.html)** — The sender of the inbound email.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the inbound email.

message\_id
: *Readonly* **[string](../../general/data_types.html)** — The value of the Message-ID header of the inbound email. This value always starts with `<` and ends with `>`.

note
: *Readonly* **[reference](../../general/data_types.html#references) to [Note](../../notes.html)** — The note that was created from the inbound email.

source\_uri
: *Readonly* **[string](../../general/data_types.html)** — An expiring URL that can be used to access the source of the inbound email for a limited time.

subject
: *Readonly* **[string](../../general/data_types.html)** — The subject of the inbound email.

to
: *Readonly* **[string](../../general/data_types.html)** — The recipient of the inbound email.
