# Custom Collection Elements API

- [List custom collection elements](index.html#list-custom-collection-elements)
- [Get a single custom collection element](index.html#get-a-custom-collection-element)
- [Create a custom collection element](index.html#create-a-custom-collection-element)
- [Update a custom collection element](index.html#update-a-custom-collection-element)
- [Fields](index.html#fields)

## List custom collection elements

List all custom collection elements for an account:

```
GET /custom_collection_elements
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"custom_collection":"collection_2","reference":"item_1","name":"Item 1","description":"1st item","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"custom_collection":"collection_2","reference":"item_2","name":"Item 2","description":"Another item","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"}]
```

The response contains [these fields](index.html#collection-element-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of custom collection elements.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/custom_collection_elements/disabled`: List all disabled custom collection elements
- `/custom_collection_elements/enabled`: List all enabled custom collection elements

### Collection Fields

By default the following fields will appear in collections of custom collection elements:

`id` `sourceID` `custom_collection` `reference` `name` `description` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `custom_collection` `source` `sourceID` `disabled` `reference` `name` `created_at` `updated_at`

### Sorting

By default a collection of custom collection elements is sorted **ascending** by `id`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `custom_collection` `reference` `created_at` `updated_at`

## Get a single custom collection element

```
GET /custom_collection_elements/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2016-12-23T05:09:03-06:00","custom_collection":"collection_2","description":"1st item","disabled":false,"id":2,"information":"The primary element","localized_description":"1st item","localized_name":"Item 1","name":"Item 1","reference":"item_1","source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](index.html#fields).

## Create a custom collection element

```
POST /custom_collection_elements
```

When creating a new custom collection element [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created custom collection and is similar to the response in [Get a single custom collection element](index.html#get-a-single-custom-collection-element)

## Update a custom collection element

```
PATCH /custom_collection_elements/:id
```

When updating a custom collection element [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated custom collection element and is similar to the response in [Get a single custom collection element](index.html#get-a-single-custom-collection-element)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the custom collection element was created.

custom\_collection
: *Readonly* **[enum](../general/enumerations/index.html)** with `reference` field of [Custom Collection](../custom_collections/index.html) — The Custom collection the custom collection element belongs to.

description
: *Optional* **[string](../general/data_types.html) (max 255)** — The Description field is used to enter a very short description of the custom collection element.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the custom collection element may not be selected in suggest boxes for custom fields.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the custom collection.

information
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Information field is used to add any additional information about the custom collection element that might prove useful.

information\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Information field.

localized\_description
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — Translated Description in the current [language](../index.html#internationalization), defaults to `description` in case no translation is provided.

localized\_name
: *Readonly* **[string](../general/data_types.html) (max 80)** — Translated Name in the current [language](../index.html#internationalization), defaults to `name` in case no translation is provided.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the custom collection element. Ideally the name of a custom collection element consists of a single word.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the custom collection element. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

reference
: *Optional* **[string](../general/data_types.html) (max 128)** — The Reference field defaults to the Name field value, written in lower case characters and with all spaces replaced by the underscore character. This reference can be used in automation rules.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the custom collection element. If the custom collection element has no updates it contains the `created_at` value.
