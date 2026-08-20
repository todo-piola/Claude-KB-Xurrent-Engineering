# Product backlogs API

- [List product backlogs](index.html#list-product-backlogs)
- [Get a single product backlog](index.html#get-a-single-product-backlog)
- [Create a product backlog](index.html#create-a-product-backlog)
- [Update a product backlog](index.html#update-a-product-backlog)
- [Fields](index.html#fields)

## List product backlogs

List all product backlogs for an account:

```
GET /product_backlogs
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2022-03-04T01:55:10-06:00","disabled":false,"id":6,"name":"My Backlog","product_goal":"Provide best expense reporting experience for employees.","product_owner":{"id":6,"name":"Howard Tanner","...":"..."},"updated_at":"2022-03-04T01:55:10-06:00","...":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of product backlogs.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/product_backlogs/disabled`: List all disabled product backlogs
- `/product_backlogs/enabled`: List all enabled product backlogs

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of product backlogs:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `created_at` `updated_at` `disabled` `service_instance` `request_template`

### Sorting

By default a collection of product backlogs is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at` `service_instance` `request_template`

## Get a single product backlog

```
GET /product_backlogs/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2022-03-04T01:55:10-06:00","disabled":false,"id":6,"name":"My Backlog","product_goal":"Provide best expense reporting experience for employees.","product_owner":{"id":6,"name":"Howard Tanner","...":"..."},"updated_at":"2022-03-04T01:55:10-06:00","...":"..."}
```

The response contains [these fields](index.html#fields).

## Create a product backlog

```
POST /product_backlogs
```

When creating a new product backlog [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created product backlog and is similar to the response in [Get a single product backlog](index.html#get-a-single-product-backlog).

## Update a product backlog

```
PATCH /product_backlogs/:id
```

When updating an product backlog [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated product backlog and is similar to the response in [Get a single product backlog](index.html#get-a-single-product-backlog).

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the product backlog was created.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to enter a high-level description of the product backlog.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the product backlog may no longer be related to other records.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the product backlog.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the product backlog.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the product backlog. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

product\_owner
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Product owner field is used to select the person responsible for maximizing the value of the work done based on this product backlog.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the product backlog. If the product backlog has no updates it contains the `created_at` value.

request\_template
: *Optional* **[reference](../general/data_types.html#references) to [Request Template](../request_templates.html)** — The Request template field is used to select the [Request template](../request_templates.html) that must be used to generate a new request in a product backlog.

service\_instance
: *Optional* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The Service instance field is used to select the [Service Instance](../service_instances/index.html) that should be used when creating requests in this product backlog.
