# Releases - Notes API

- [List notes of a release](index.html#list-notes-of-a-release)
- [Create a note](index.html#create-a-note)
- [Fields](index.html#fields)

## List notes of a release

List all [notes](../../notes.html) of the release with a specific ID.

```
GET /releases/:id/notes
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-04-27T05:24:00-05:00","person":{"name":"Frank Watson","id":46},"attachments":[],"text":"The objective of this release is to automate the update of the exchange rate data in the Expense service Production using the \"Exchange Rate API\":http://www.exchangerate-api.com/ cloud service.","id":534},{"...":"..."}]
```

The response contains [these fields](../../notes.html#collection-fields) by default.

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](../../notes.html#fields):

`created_at` `medium` `person`

## Create a note

```
POST /releases/:id/notes
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
