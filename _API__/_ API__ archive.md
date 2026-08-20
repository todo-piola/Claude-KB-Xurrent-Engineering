# Archive API

- [List archive](index.html#list-archive)
- [Get a single archive item](index.html#get-a-single-archive-item)
- [Fields](index.html#fields)

## List archive

List all archive items for an account:

```
GET /archive
```

### Response

```
status: 200 OK
```

```
[{"id":6,"created_at":"2018-07-05T05:01:42-05:00","archived_by":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"archived":"request","request":{"id":70394,"href":"/requests/70394","display_name":"70394 Windows password reset required"}},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the archive collection.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of archive:

`id` `created_at` `archived_by` `archived`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `created_at`

### Sorting

By default a collection of archive is sorted **descending** by `created_at`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `created_at`

## Get a single archive item

```
GET /archive/:id
```

### Response

```
status: 200 OK
```

```
{"id":6,"created_at":"2018-07-05T05:01:42-05:00","archived_by":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"archived":"request","request":{"id":70394,"href":"/requests/70394","display_name":"70394 Windows password reset required"}}
```

The response contains [these fields](index.html#fields).

## Fields

archived
: *Readonly* **[string](../general/data_types.html) (max 80)** — The Archived field contains the record type of the archived record, e.g. request. A field with this name is added that contains the reference to the archived record.

archived\_by
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Archived by field is used to select the person who archived the record.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the archive was created.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the archive.
