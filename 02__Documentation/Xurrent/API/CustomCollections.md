# Custom Collections API

- [List custom collections](index.html#list-custom-collections)
- [Get a single custom collection](index.html#get-a-custom-collection)
- [Create a custom collection](index.html#create-a-custom-collection)
- [Update a custom collection](index.html#update-a-custom-collection)
- [Fields](index.html#fields)

## List Custom Collections

List all custom collections for an account:

```
GET /custom_collections
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"reference":"collection_2","name":"Collection 2","description":"2nd collection","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"reference":"another_collection","name":"Another Collection","description":"Different collection","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"}]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of custom collections.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/custom_collections/disabled`: List all disabled custom collections
- `/custom_collections/enabled`: List all enabled custom collections

### Collection Fields

By default the following fields will appear in collections of custom collections:

`id` `sourceID` `reference` `name` `description` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `disabled` `reference` `created_at` `updated_at`

The filters on `source`, `sourceID`, and `reference` are not case sensitive.

### Sorting

By default a collection of custom collections is sorted **ascending** by `id`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `reference` `created_at` `updated_at`

## Get a single custom collection

```
GET /custom_collections/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2016-12-23T05:09:03-06:00","description":"2nd collection","disabled":false,"id":2,"name":"Collection 2","reference":"collection_2","source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](index.html#fields).

## Create a custom collection

```
POST /custom_collections
```

When creating a new custom collection [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created custom collection and is similar to the response in [Get a single custom collection](index.html#get-a-single-custom-collection)

## Update a custom collection

```
PATCH /custom_collections/:id
```

When updating a custom collection [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated custom collection and is similar to the response in [Get a single custom collection](index.html#get-a-single-custom-collection)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the custom collection was created.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to enter a high-level description of the custom collection.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the custom collection may not be related to any more custom views.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the custom collection.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the custom collection.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the custom collection. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

reference
: *Optional* **[string](../general/data_types.html) (max 128)** — The Reference field defaults to the Name field value, written in lower case characters and with all spaces replaced by the underscore character. This reference can be used to link the custom collection to a custom collection element using the Xurrent APIs or the Xurrent Import functionality and in automation rules.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

ui\_extension
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field is used to select the UI extension that is to be added to the custom collection elements that are based on the custom collection.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the custom collection. If the custom collection has no updates it contains the `created_at` value.
