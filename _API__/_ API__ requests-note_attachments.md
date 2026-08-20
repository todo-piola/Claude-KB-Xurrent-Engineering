# Requests - Note attachments API

- [List note attachments of a request](../note_attachments.html#list-notes-of-a-request)
- [Fields](../note_attachments.html#fields)

## List note attachments of a request

List all attachments of all notes of a request with a specific ID.

```
GET /requests/:id/note_attachments
```

### Response

```
status: 200 OK
```

```
[{"id":3,"created_at":"2024-03-14T07:27:40-05:00","name":"my-attachment.txt","key":"attachments/5/2024/03/14/6/1710433637.372055-976f080fe40a9f78f087bdbb268dc9bd671532f4178249e41e1d9eda4633e0c4/my-attachment.txt","uri":"https://...","inline":false,"size":147491,"account":{"id":"weu-it","name":"Widget Europe - IT"},"nodeID":"...","note":{"id":3849,"nodeID":"..."}},"..."]
```

The response contains [these fields](../note_attachments.html#collection-fields) by default.

### Collection Fields

By default the following [fields](../note_attachments.html#fields) will appear in collections of note attachments:

`created_at` `id` `inline` `key` `name` `note` `size` `uri`

Obtain a different set of [fields](../note_attachments.html#fields) using the [?fields= parameter](../../general/field_selection/index.html#collection-of-resources).
The `note` field will always be present, regardless of the value of the `fields` parameter.

### Sorting

The collection of note attachments is sorted **ascending** by `id`.

The following [fields](../note_attachments.html#fields) are accepted by the [?sort= parameter](../../general/ordering.html):

`id` `created_at`

## Fields

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the attachment was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the attachment.

inline
: *Readonly* **[boolean](../../general/data_types.html)** — Whether the attachment is an inline image.

key
: *Readonly* **[string](../../general/data_types.html)** — Storage key of the attachment.
 When the attachment is an inline image, the key can be used to match the attachment to an inline image included in the related note.

name
: *Readonly* **[string](../../general/data_types.html)** — The filename of the attachment.

note
: *Readonly* **[reference](../../general/data_types.html#references) to [Note](../../notes.html)** — The note that this attachment is related to.

size
: *Readonly* **[integer](../../general/data_types.html)** — The size in bytes of the attachment.

uri
: *Readonly* **[string](../../general/data_types.html)** — An expiring URL that can be used to access the attachment for a limited time.
