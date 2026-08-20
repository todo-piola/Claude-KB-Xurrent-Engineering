# Audit Entries API

- [List audit entries](../audit_entries.html#list-audit-entries)
- [Get a single audit entry](../audit_entries.html#get-a-single-audit-entry)
- [Fields](../audit_entries.html#fields)

## List audit entries

List all audit entries for an account:

```
GET /audit_lines
```

### Response

```
status: 200 OK
```

```
[{"id":354217,"action":"update","created_at":"2017-01-21T14:47:11-06:00","created_by":{"id":156,"name":"Ellen Brown","account":{"id":"widget","name":"Widget International"}},"audited":"project","project":{"id":7497,"subject":"Digital Operations Center (DOC)"}},{"id":354216,"action":"create","created_at":"2017-01-21T14:46:47-06:00","created_by":{"id":128,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"audited":"request","request":{"id":70486,"subject":"Unable to access SAP"}},"..."]
```

The response contains [these fields](../audit_entries.html#collection-fields) by default. [Filtering](../audit_entries.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of audit entries.

### Collection Fields

By default the following fields will appear in collections of Audit Entries:

`action` `auditable` `audited` `created_at` `created_by` `id`

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../audit_entries.html#fields):

`id` `created_at`

### Sorting

By default a collection of Audit Entries is sorted **descending** by `id`.
The following [field](../audit_entries.html#fields) is accepted by the [?sort= parameter](../general/ordering.html):

`id`

## Get a single audit entry

```
GET /audit_lines/:id
```

### Response

```
status: 200 OK
```

```
{"id":354217,"action":"update","created_at":"2017-01-21T14:47:11-06:00","created_by":{"id":156,"name":"Ellen Brown","account":{"id":"widget","name":"Widget International"}},"audited":"project","project":{"id":7497,"subject":"Digital Operations Center (DOC)"},"changes":{"justification":["compliance","correction"]}}
```

The response contains [these fields](../audit_entries.html#fields).

## Fields

action
: *Readonly* **[enum](../general/enumerations/index.html)** — The Action field indicates the type of transactions that caused the audit entry to be generated. Possible values are:
: - `create`: Create
 - `update`: Update
 - `destroy`: Destroy
 - `info`: Info

auditable
: *Readonly* **[reference](../general/data_types.html#references)** — A reference to the record for which the audit entry was generated. The field name in the response matches the value of the `audited` field (e.g. when `audited` is `request`, the reference is returned as `request`).

audited
: *Readonly* **[enum](../general/enumerations/index.html)** — The Audited field contains the record type name of the record for which the audit entry was generated.

changes
: *Readonly* **hash** — The old and the new value of each field that was set or changed by the transaction that caused the audit entry to be generated. Only available when [getting a single audit entry](../audit_entries.html#get-a-single-audit-entry), not included in [collection listings](../audit_entries.html#list-audit-entries).

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the audit entry was created.

created\_by
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Created by field is set to the person who caused the audit entry to be generated.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the audit entry.

user
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The User field is set to the person whose session was used to cause the audit entry to be generated. This is usually the same person as the one in the Created by field, but can be different when a support user performed the action using an impersonation session.
