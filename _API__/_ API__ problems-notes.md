# Problems - Notes API

- [List notes of a problem](index.html#list-notes-of-a-problem)
- [Create a note](index.html#create-a-note)
- [Fields](index.html#fields)

## List notes of a problem

List all [notes](../../notes.html) of the problem with a specific ID.

```
GET /problems/:id/notes
```

### Response

```
status: 200 OK
```

```
[{"person":{"name":"Barney Turban","id":58},"created_at":"2016-03-12T11:33:00-06:00","text":"Use the information gathered in the previous risk & impact analysis tasks to finalize the change plan. Do this is such a way that the implementation plan minimizes both the risk of failure and the impact on the customer(s). Also ensure that the necessary approvals are collected before the implementation of the change can start.\n\nNote that approval from the owner of the service that is related to the workflow is required for each non-standard change, regardless of whether customer representative approval is required or not. Approval from the customer representative(s) of the service that is related to the workflow is only required if the change implementation is going to cause:\n- the service to become unavailable or degraded during service hours, or\n- the functionality of the service to become different.","id":464,"medium":"default","task":{"id":89,"subject":"Finalize the change plan"},"attachments":[]},{"person":{"name":"Luis Thomas","id":60},"created_at":"2016-03-12T11:33:00-06:00","text":"Because the servers are monitored by NNM and because they will need to be rebooted after the upgrade, events wil be generated, and we should warn Operations.","id":463,"medium":"default","task":{"id":88,"subject":"Will events be generated when the change is implemented?"},"attachments":[]},"..."]
```

The response contains [these fields](../../notes.html#collection-fields) by default.

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](../../notes.html#fields):

`created_at` `medium` `person`

## Create a note

```
POST /problems/:id/notes
```

When creating a new note the `text` field must be supplied.

### Response

```
status: 201 Created
```

```
{"id":12345}
```

The response contains the `id` of the created note.

## Fields

text
: *Required* **[text](../../general/data_types.html) (max 64KB)** — The text of the note.

attachments
: *Optional* **[attachments](../../general/data_types.html#attachments)** Attachments that should be added to the note.

suppress\_note\_added\_notifications
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — Set to the value `true` to suppress the ‘Note Added’ notifications from being created. Other notifications, such as ‘Watchlist Item Updated’ and ‘Person Mentioned’, will still be created if applicable.
