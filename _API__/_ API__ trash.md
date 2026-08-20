# Trash API

- [List trash](index.html#list-trash)
- [Get a single trash item](index.html#get-a-single-trash-item)
- [Fields](index.html#fields)

## List trash

List all trash items for an account:

```
GET /trash
```

### Response

```
status: 200 OK
```

```
[{"id":6,"created_at":"2018-07-05T05:01:42-05:00","trashed_by":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"trashed":"request","request":{"id":70394,"href":"/requests/70394","display_name":"70394 Windows password reset required"}},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the trash collection.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of trash:

`id` `created_at` `trashed_by` `trashed`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `created_at`

### Sorting

By default a collection of trash is sorted **descending** by `created_at`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `created_at`

## Get a single trash item

```
GET /trash/:id
```

### Response

```
status: 200 OK
```

```
{"id":6,"created_at":"2018-07-05T05:01:42-05:00","trashed_by":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"trashed":"request","request":{"id":70394,"href":"/requests/70394","display_name":"70394 Windows password reset required"}}
```

The response contains [these fields](index.html#fields).

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the trash was created.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the trash.

trashed
: *Readonly* **[string](../general/data_types.html) (max 80)** — The Trashed field contains the record type of the trashed record, e.g. request. A field with this name is added that contains the reference to the trashed record.

trashed\_by
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Trashed by field is used to select the person who trashed the record.
