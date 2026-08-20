# Product Categories API

- [List product categories](index.html#list-product-categories)
- [Get a single product category](index.html#get-a-single-product-category)
- [Create a product category](index.html#create-a-product-category)
- [Update a product category](index.html#update-a-product-category)
- [Fields](index.html#fields)

## List product categories

List all product categories for an account:

```
GET /product_categories
```

### Response

```
status: 200 OK
```

```
[{"id":301,"sourceID":null,"name":"IP Address","group":"Address","reference":"address/ip_address","rule_set":"logical_asset_without_financial_data","created_at":"2015-09-10T12:15:16-05:00","updated_at":"2015-09-14T12:31:27-05:00","localized_group":"Address","localized_name":"IP Address"},{"id":312,"sourceID":null,"name":"Desktop PC or Workstation","group":"Computer","reference":"computer/desktop_pc_or_workstation","rule_set":"physical_asset","created_at":"2015-09-10T12:15:16-05:00","updated_at":"2015-09-10T12:15:16-05:00","localized_group":"Computer","localized_name":"Desktop PC or Workstation"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of product categories.

### Collection Fields

By default the following fields will appear in collections of product categories:

`id` `sourceID` `name` `group` `rule_set` `reference` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `reference` `rule_set` `created_at` `updated_at` `disabled` `name`

The filters on `source`, `sourceID`, `reference` and `name` are not case sensitive.

### Sorting

By default a collection of product categories is sorted **ascending** by `name`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `rule_set` `reference` `created_at` `updated_at`

## Get a single product category

```
GET /product_categories/:id
```

### Response

```
status: 200 OK
```

```
{"id":312,"source":"4me","sourceID":null,"name":"Desktop PC or Workstation","disabled":false,"picture_uri":null,"group":"Computer","reference":"computer/desktop_pc_or_workstation","rule_set":"physical_asset","created_at":"2015-09-10T12:15:16-05:00","updated_at":"2015-09-10T12:15:16-05:00","localized_group":"Computer","localized_name":"Desktop PC or Workstation"}
```

The response contains [these fields](index.html#fields).

## Create a product category

```
POST /product_categories
```

When creating a new product category [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created product category and is similar to the response in [Get a single product category](index.html#get-a-single-product-category)

## Update a product category

```
PATCH /product_categories/:id
```

When updating a product category [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated product category and is similar to the response in [Get a single product category](index.html#get-a-single-product-category)

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the product category was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the product category may not be related to any more products.

group
: *Required* **[string](../general/data_types.html) (max 255)** — The Group field is used to include the product category in a group.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the product category.

localized\_group
: *Readonly* **[string](../general/data_types.html) (max 64KB)** — Translated Group in the current [language](../index.html#internationalization), defaults to `group` in case no translation is provided.

localized\_name
: *Readonly* **[string](../general/data_types.html) (max 255)** — Translated Name in the current [language](../index.html#internationalization), defaults to `name` in case no translation is provided.

name
: *Required* **[string](../general/data_types.html) (max 255)** — The Name field is used to enter the name of the product category.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the product category. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

reference
: *Readonly* **[string](../general/data_types.html) (max 80)** — The Reference field is automatically set to the concatenation of the Group field value and the Name field value, separated by a forward slash, written in lower case characters and with all spaces replaced by an underscore character.

review\_end\_of\_support\_days
: *Optional* **[integer](../general/data_types.html)** — Number of days before a configuration item’s end-of-support date after which a lifecycle review is flagged. Leave empty to disable this review.

review\_in\_use\_since\_days
: *Optional* **[integer](../general/data_types.html)** — Number of days after a configuration item’s in-use-since date after which a lifecycle review is flagged. Leave empty to disable this review.

review\_last\_seen\_days
: *Optional* **[integer](../general/data_types.html)** — Number of days since a configuration item was last seen after which a lifecycle review is flagged. Leave empty to disable this review.

review\_license\_expiry\_days
: *Optional* **[integer](../general/data_types.html)** — Number of days before a configuration item’s license-expiry date after which a lifecycle review is flagged. Leave empty to disable this review.

review\_warranty\_expiry\_days
: *Optional* **[integer](../general/data_types.html)** — Number of days before a configuration item’s warranty-expiry date after which a lifecycle review is flagged. Leave empty to disable this review.

rule\_set
: *Required* **[enum](../general/enumerations/index.html)**, default: `none` — The Rule set field is used to select a set of rules that are to be applied to the products to which the product category is related, as well as the configuration items that are related to those products. The selected rule set dictates which fields are available for these product and configuration items. Valid values are:
: - `physical_asset`: Physical Asset
 - `logical_asset_with_financial_data`: Logical Asset with Financial Data
 - `logical_asset_without_financial_data`: Logical Asset without Financial Data
 - `server`: Server
 - `software`: Software
 - `software_distribution_package`: Software Distribution Package

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

ui\_extension
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field is used to select the UI extension that is to be added to the products that are based on the product category.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the product category. If the product category has no updates it contains the `created_at` value.
