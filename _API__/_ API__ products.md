# Products API

- [List products](../products.html#list-products)
- [Get a single product](../products.html#get-a-single-product)
- [Create a product](../products.html#create-a-product)
- [Update a product](../products.html#update-a-product)
- [Fields](../products.html#fields)

## List products

List all products for an account:

```
GET /products
```

### Response

```
status: 200 OK
```

```
[{"name":"Adobe Reader","created_at":"2016-03-14T03:10:50-06:00","category":"software/browser_viewer_application","sourceID":null,"updated_at":"2016-03-14T03:10:50-06:00","service":{"name":"Personal Computing","id":22,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"support_team":{"name":"End-User Support, Houston","id":9},"id":33},{"name":"APC NetShelter SX 48U Rack","created_at":"2016-03-14T03:10:50-06:00","category":"rack_enclosure","sourceID":null,"updated_at":"2016-03-14T03:10:50-06:00","service":{"name":"Rack Space","id":26,"provider":{"name":"Widget Data Center, External IT","id":30}},"support_team":{"name":"Unix Servers","id":13},"id":34,"disabled":true},"..."]
```

The response contains [these fields](../products.html#collection-fields) by default. [Filtering](../products.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of products.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/products/disabled`: List all disabled products
- `/products/enabled`: List all enabled products
- `/products/supported_by_my_teams`: List all products which support team is one of the teams that the API user is a member of

### Collection Fields

By default the following [fields](../products.html#fields) will appear in collections of products:

`id` `sourceID` `name` `category` `support_team` `service` `created_at` `updated_at`

Obtain a different set of [fields](../products.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../products.html#fields):

`id` `source` `sourceID` `name` `disabled` `category` `rule_set` `support_team` `service` `created_at` `updated_at`

### Sorting

By default a collection of products is sorted **ascending** by `name`.

The following [fields](../products.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `support_team` `service` `created_at` `updated_at`

### Response

The response is similar to the response in [List products](../products.html#list-products)

## Get a single product

```
GET /products/:id
```

### Response

```
status: 200 OK
```

```
{"picture_uri":"https://itrp-demo.s3.amazonaws.com/defaults/avatars/products/large/Adobe Reader.png","name":"Adobe Reader","model":null,"rule_set":"software","financial_owner":null,"brand":"Adobe","remarks":"No license required.","created_at":"2016-03-14T03:10:50-06:00","category":"software/browser_viewer_application","sourceID":null,"updated_at":"2016-03-14T03:10:50-06:00","supplier":null,"service":{"name":"Personal Computing","id":22,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"support_team":{"name":"End-User Support, Houston","id":9},"rate":null,"useful_life":null,"id":33,"source":null,"depreciation_method":"na_cost_is_zero","ui_extension":null,"disabled":false}
```

The response contains [these fields](../products.html#fields).

## Create a product

```
POST /products
```

When creating a new product [these fields](../products.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"brand":"...","...":"..."}
```

The response contains [all fields](../products.html#fields) of the created product and is similar to the response in [Get a single product](../products.html#get-a-single-product)

## Update a product

```
PATCH /products/:id
```

When updating a product [these fields](../products.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"brand":"...","...":"..."}
```

The response contains [all fields](../products.html#fields) of the updated product and is similar to the response in [Get a single product](../products.html#get-a-single-product)

## Fields

attachments
: *Readonly* **aggregated Attachments**

brand
: *Required* **[string](../general/data_types.html) (max 128)** — The Brand field is used to select a previously entered brand name or to enter a new one. The brand name is typically the name of the product’s manufacturer.

category
: *Required* **[enum](../general/enumerations/index.html)** with `reference` field of [Product Categories](../product_categories/index.html) — The Category field is used to select the appropriate product category for the product.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the product was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the related product category.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

depreciation\_method
: *Optional* **[enum](../general/enumerations/index.html)** — The Depreciation method field is used to specify whether or not configuration items that are based on the product are typically depreciated and if so, which depreciation method is normally applied.
 Valid values are:

 - `not_depreciated`: Not Depreciated
 - `double_declining_balance`: Double Declining Balance
 - `reducing_balance`: Reducing Balance (or Diminishing Value)
 - `straight_line`: Straight Line (or Prime Cost)
 - `sum_of_the_years_digits`: Sum of the Year’s Digits

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the product may no longer be used to register new configuration items.

financial\_owner
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Financial owner field is used to select the internal organization which budget is normally used to obtain the product.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the product.

model
: *Required* **[string](../general/data_types.html) (max 128)** — The Model field is used to enter the model of the product.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the product. Fill out the Brand, Model, Product ID (optional) and Category fields to automatically generate a name based on the values entered in these fields.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the product. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

productID
: *Optional* **[string](../general/data_types.html) (max 128)** — The Product ID field is used to enter the unique identifier of the product that is used by the manufacturer. The concatenation of Brand and Product ID must be unique within a Xurrent account.

rate
: *Optional* **[integer](../general/data_types.html)** — The Rate field is used to specify the yearly rate that should normally be applied to calculate the depreciation of configuration items that are based on the product using the reducing balance (or diminishing value) method.

recurrence
: *Optional* **aggregated** — The recurrence settings hash, missing in case the product has no recurrency defined. It contains the fields of a [Recurrence](../recurrences.html), except the following:
: `start_date` `end_date` `next_occurrence_at` `last_occurrence_at` `last_occurrence_object` `last_occurrence_errors` `ical`

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to enter any additional information about the product that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Remarks field.

rule\_set
: *Readonly* **[enum](../general/data_types.html)** — The Rule set field is automatically set to the rule set of the related product category. Valid values are:
: - `logical_asset_with_financial_data`: Logical Asset with Financial Data
 - `logical_asset_without_financial_data`: Logical Asset without Financial Data
 - `physical_asset`: Physical Asset
 - `server`: Server
 - `software`: Software
 - `software_distribution_package`: Software Distribution Package

salvage\_value
: *Optional* **[decimal](../general/data_types.html)** — The Salvage value field is used to enter the value for the configuration items based on this product at the end of its useful life (i.e. at the end of its depreciation period). When a value is not specified for this field, it is set to zero.

salvage\_value\_currency
: *Optional* **[enum](../general/enumerations/index.html)** — The currency of the Salvage value field value of the configuration items based on this product. For valid values, see the list of currencies in the Currency field of the [Account API](../account.html).

service
: *Optional* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the [Service](../services.html) which [Service Instances](../service_instances/index.html) would typically include the product.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the [Organization](../organizations.html) from which the product is typically obtained. If the product is developed internally, select the internal organization that develops it. Note that a lease company should be selected in this field if the product is normally leased.

support\_team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Support team field is used to select the [Team](../teams.html) responsible for maintaining the product’s information in the configuration management database (CMDB).

ui\_extension
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field is used to select the UI extension that is to be added to the configuration items that are based on the product.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the product. If the product has no updates it contains the `created_at` value.

useful\_life
: *Optional* **[integer](../general/data_types.html)** — The Useful life field is used to enter the number of years within which configuration items that are based on the product are typically depreciated.

workflow\_template
: *Optional* **[reference](../general/data_types.html#references) to [Workflow Template](../workflow_templates.html)** — The workflow template that is used to periodically maintain configuration items created from the product.

workflow\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The person who will be responsible for coordinating the workflows that will be generated automatically in accordance with the recurrence schedule.
