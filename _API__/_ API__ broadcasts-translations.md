# Broadcast Translations API

- [List broadcast translations](index.html#list-broadcast-translations)
- [Get a single broadcast translation](index.html#get-a-single-broadcast-translation)
- [Create a broadcast translation](index.html#create-a-broadcast-translation)
- [Update a broadcast translation](index.html#update-a-broadcast-translation)
- [Remove a broadcast translation](index.html#remove-a-broadcast-translation)
- [Fields](index.html#fields)

## List broadcast translations

List all broadcast translations for a Broadcast:

```
GET /broadcasts/:broadcast_id/translations
```

### Response

```
status: 200 OK
```

```
[{"id":23,"locale":"de","created_at":"2016-05-23T09:35:52-05:00","updated_at":"2016-05-23T09:35:52-05:00"},{"id":18,"locale":"en-US","created_at":"2016-05-22T03:20:36-05:00","updated_at":"2016-05-26T06:13:56-05:00"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../../general/pagination.html) are available to reduce/limit the collection of broadcast translations.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of broadcast translations:

`id` `locale` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `locale` `created_at` `updated_at`

### Sorting

By default a collection of broadcast translations is sorted **descending** by `created_at`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../../general/ordering.html):

`id` `locale` `message` `created_at` `updated_at`

## Get a single broadcast translation

```
GET /broadcasts/:broadcast_id/translations/:id
```

### Response

```
status: 200 OK
```

```
{"id":18,"locale":"en-US","message":"SAP will be down for maintenance this Sunday between 5am and 7am.","created_at":"2016-05-22T03:20:36-05:00","updated_at":"2016-05-26T06:13:56-05:00"}
```

The response contains [these fields](index.html#fields).

## Create a broadcast translation

```
POST /broadcasts/:broadcast_id/translations
```

When creating a new broadcast translation [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"message":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created broadcast translation and is similar to the response in [Get a single broadcast translation](index.html#get-a-single-broadcast-translation)

## Update a broadcast translation

```
PATCH /broadcasts/:broadcast_id/translations/:id
```

When updating a broadcast translation [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"message":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated broadcast translation and is similar to the response in [Get a single broadcast translation](index.html#get-a-single-broadcast-translation)

## Remove a broadcast translation

```
DELETE /broadcasts/:broadcast_id/translations/:id
```

### Response

```
status: 204 No Content
```

## Fields

attachments
: *Readonly* **aggregated Attachments**

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the broadcast translation.

locale
: *Optional* **[string](../../general/data_types.html) (max 5)**

message
: *Required* **[text](../../general/data_types.html) (max 64KB)** — The Message field is used to enter the information that is to be broadcasted.

message\_attachments
: *Writeonly* **[attachments](../../general/data_types.html#attachments)** The attachments used in the Message field.

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the broadcast translation was created.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the broadcast translation. If the broadcast translation has no updates it contains the `created_at` value.
