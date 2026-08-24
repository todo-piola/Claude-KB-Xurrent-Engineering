# Service Categories API

- [List service categories](index.html#list-service-categories)
- [Get a single service category](index.html#get-a-single-service-category)
- [Create a service category](index.html#create-a-service-category)
- [Update a service category](index.html#update-a-service-category)
- [Remove a service category](index.html#remove-a-service-category)
- [Fields](index.html#fields)

## List service categories

List all service categories for an account:

```
GET /service_categories
```

### Response

```
status: 200 OK
```

```
[{"id":1,"sourceID":null,"name":"Enterprise Applications","created_at":"2014-01-30T09:07:00-06:00","updated_at":"2014-01-30T09:07:41-06:00","localized_name":"Enterprise Applications"},{"id":2,"sourceID":null,"name":"Printing","created_at":"2014-01-30T09:08:34-06:00","updated_at":"2014-01-30T09:08:34-06:00","localized_name":"Printing"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of service categories.

### Collection Fields

By default the following fields will appear in collections of service categories:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `created_at` `updated_at`

The filters on `source`, `sourceID` and `name` are not case sensitive.

### Sorting

By default a collection of service categories is sorted **ascending** by `name`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single service category

```
GET /service_categories/:id
```

### Response

```
status: 200 OK
```

```
{"id":6,"source":"4me","sourceID":null,"name":"Enterprise Applications","localized_name":"Enterprise Applications","description":"These are the software application services that are used for the support of Widget's core and non-core business processes. They do not include the Email service or the applications that run on PCs or mobile devices without network connectivity.","localized_description":"These are the software application services that are used for the support of Widget's core and non-core business processes. They do not include the Email service or the applications that run on PCs or mobile devices without network connectivity.","picture_uri":null,"created_at":"2014-01-30T09:07:00-06:00","updated_at":"2014-01-30T09:07:41-06:00","services":[{"id":18,"name":"Customer Relationship Management (Siebel)","localized_name":"Customer Relationship Management (Siebel)","provider":{"id":32,"name":"Widget Data Center, External IT"}},"..."]}
```

The response contains [these fields](index.html#fields).

## Create a service category

```
POST /service_categories
```

When creating a new service category [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created service category and is similar to the response in [Get a single service category](index.html#get-a-single-service-category)

## Update a service category

```
PATCH /service_categories/:id
```

When updating a service category [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated service category and is similar to the response in [Get a single service category](index.html#get-a-single-service-category)

## Remove a service category

Remove a service category with a specific ID.

```
DELETE /service_categories/:id
```

### Response

```
status: 204 No Content
```

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the service category was created.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to enter a high-level description of the type of services that are included in the service category.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the service category.

localized\_description
: *Readonly* **[string](../general/data_types.html) (max 64KB)** — Translated Description in the current [language](../index.html#internationalization), defaults to `description` in case no translation is provided.

localized\_name
: *Readonly* **[string](../general/data_types.html) (max 255)** — Translated Name in the current [language](../index.html#internationalization), defaults to `name` in case no translation is provided.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the service category.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the service category. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the service category. If the service category has no updates it contains the `created_at` value.
