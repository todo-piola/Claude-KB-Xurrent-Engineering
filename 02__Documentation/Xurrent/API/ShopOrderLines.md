# Shop Order Lines API

- [List shop order lines](index.html#list-shop-order-lines)
- [Get a single shop order line](index.html#get-a-single-shop-order-line)
- [Create a shop order line](index.html#create-a-shop-order-line)
- [Update a shop order line](index.html#update-a-shop-order-line)
- [Fields](index.html#fields)

## List shop order lines

List all shop order lines for an account:

```
GET /shop_order_lines
```

### Response

```
status: 200 OK
```

```
[{"completed_at":null,"created_at":"2022-11-29T04:20:13-06:00","id":4,"name":"HP Compaq 6730s","ordered_at":"2022-11-29T04:20:32-06:00","quantity":3,"requested_for":{"id":96,"name":"Beatrice Baldwin","account":{"id":"widget","name":"Widget International"},"nodeID":"..."},"shop_article":"HPC6730s","sourceID":null,"status":"fulfillment_pending","updated_at":"2022-11-30T03:57:05-06:00","nodeID":"..."},{"completed_at":null,"created_at":"2022-11-24T08:11:22-06:00","id":1,"name":"Dell Precision M4400","ordered_at":null,"quantity":1,"requested_for":{"id":239,"name":"Heinrich Čihař","account":{"id":"widget","name":"Widget International"},"nodeID":"..."},"shop_article":"DellM4400","sourceID":null,"status":"in_cart","updated_at":"2022-11-24T08:11:22-06:00","nodeID":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of shop order lines.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/shop_order_lines/open`: List all shop order lines that are not completed
- `/shop_order_lines/completed`: List all shop order lines that are completed
- `/shop_order_lines/canceled`: List all shop order lines that are canceled
- `/shop_order_lines/personal`: List all shop order lines that are requested by me

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of shop order lines:

`id`, `sourceID`, `requested_for`, `shop_article`, `name`, `status`, `quantity`, `ordered_at`, `completed_at`, `created_at`, `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID`, `status`, `completed_at`, `created_at` `updated_at`

### Sorting

By default a collection of shop order lines is sorted **ascending** by `id`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID`, `status`, `completed_at`, `created_at` `updated_at`

## Get a single shop order line

```
GET /shop_order_lines/:id
```

### Response

```
status: 200 OK
```

```
{"completed_at":null,"created_at":"2022-11-29T04:20:13-06:00","custom_fields":[{"id":"color","value":"green"}],"delivery_address":"1919 Briar Oaks Lane","delivery_city":"Houston","delivery_country":"US","delivery_state":"TX","delivery_zip":"77027","fulfillment_request":{"id":90659,"subject":"HP Compaq 6730s","nodeID":"..."},"fulfillment_task":{"id":32070,"subject":"HP Compaq 6730s","nodeID":"..."},"fulfillment_template":{"id":1401,"subject":"Deliver Shop Article","localized_subject":"Deliver Shop Article","nodeID":"..."},"id":4,"name":"HP Compaq 6730s","order":{"id":90658,"subject":"Order for 'HP Compaq 6730s'","nodeID":"..."},"ordered_at":"2022-11-29T04:20:32-06:00","price":"799.0","price_currency":"usd","provider_ordered_at":"2022-11-29T04:20:32-06:00","provider_price":"799.0","provider_price_currency":"usd","provider_recurring_period":null,"provider_recurring_price":null,"provider_recurring_price_currency":null,"provider_total_price":"2397.0","provider_total_recurring_price":null,"quantity":3,"recurring_period":null,"recurring_price":null,"recurring_price_currency":null,"requested_for":{"id":96,"name":"Beatrice Baldwin","account":{"id":"widget","name":"Widget International"},"nodeID":"..."},"shop_article":"HPC6730s","source":"4me","sourceID":null,"status":"fulfillment_pending","total_price":"2397.0","total_recurring_price":null,"updated_at":"2022-11-30T03:57:05-06:00","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Create a shop order line

```
POST /shop_order_lines
```

When creating a new shop order line [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created shop order line and is similar to the response in [Get a single shop order line](index.html#get-a-single-shop-order-line)

## Update a shop order line

```
PATCH /shop_order_lines/:id
```

When updating a shop order line, the available fields depend on the current status:

- `in_cart`: `requested_for`, `quantity`, `custom_fields`
- `fulfillment_pending`: `custom_fields`

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated shop order line and is similar to the response in [Get a single shop order line](index.html#get-a-single-shop-order-line)

## Fields

completed\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the shop order line was completed.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the shop order line was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the ordered shop article.

delivery\_address
: *Readonly* **[string](../general/data_types.html) (max 1024)** — The delivery address lines.

delivery\_city
: *Readonly* **[string](../general/data_types.html) (max 128)** — The delivery city name.

delivery\_country
: *Readonly* **[string](../general/data_types.html) (max 128)** — The delivery country name.

delivery\_state
: *Readonly* **[string](../general/data_types.html) (max 30)** — The delivery state name.

delivery\_zip
: *Readonly* **[string](../general/data_types.html) (max 20)** — The delivery zip code.

fulfillment\_request
: *Readonly* **[reference](../general/data_types.html#references) to [Request](../requests.html)** — The request generated for the fulfillment of this shop order line.

fulfillment\_task
: *Readonly* **[reference](../general/data_types.html#references) to [Task](../tasks.html)** — The fulfillment task in the order workflow related to this shop order line.

fulfillment\_template
: *Readonly* **[reference](../general/data_types.html#references) to [Request Template](../request_templates.html)** — The request template linked to the fulfillment task used to generate the fulfillment request.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the shop order line.

name
: *Readonly* **[string](../general/data_types.html) (max 128)** — The Name of the shop order line.

order
: *Readonly* **[reference](../general/data_types.html#references) to [Request](../requests.html)** — The order request related to this shop order line.

ordered\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the shop article was ordered. This corresponds to the time the order request was registered by the user.

price
: *Readonly* **[decimal](../general/data_types.html)** — The price to be charged per unit at the time the shop article was ordered.

price\_currency
: *Readonly* **[reference](../general/data_types.html#currency)** — The currency of the price.

recurring\_period
: *Readonly* **[enum](../general/enumerations/index.html)** — The Recurring period field is used to select the interval for the recurring price. Valid values are:
: - `monthly`: Monthly
 - `yearly`: Yearly

recurring\_price
: *Readonly* **[decimal](../general/data_types.html)** — The recurring price to be charged recurrently per unit for the shop article that was ordered.

recurring\_price\_currency
: *Readonly* **[reference](../general/data_types.html#currency)** — The currency of the recurrent price.

provider\_ordered\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the shop article was ordered at the provider. This corresponds to the time at which the fulfillment request was generated.

provider\_price
: *Readonly* **[decimal](../general/data_types.html)** — The price to be charged by the provider per unit at the time the shop article was ordered.

provider\_price\_currency
: *Readonly* **[reference](../general/data_types.html#currency)** — The currency of the provider price.

provider\_recurring\_period
: *Readonly* **[enum](../general/enumerations/index.html)** — The Recurring period field is used to select the interval for the provider recurring price. Valid values are:
: - `monthly`: Monthly
 - `yearly`: Yearly

provider\_recurring\_price
: *Readonly* **[decimal](../general/data_types.html)** — The recurring price to be charged recurrently per unit by the provider for the shop article that was ordered.

provider\_recurring\_price\_currency
: *Readonly* **[reference](../general/data_types.html#currency)** — The currency of the provider recurrent price.

quantity
: *Required* **[decimal](../general/data_types.html)**, default: `1` — The Quantity field is used to enter the number of units of the shop article that is being ordered.

provider\_total\_price
: *Readonly* **[decimal](../general/data_types.html)** — The total (non-recurrent) price to be charged by the provider for all units combined.

provider\_total\_recurring\_price
: *Readonly* **[decimal](../general/data_types.html)** — The total yearly recurrent price to be charged by the provider for all units combined.

requested\_by
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The person who submitted the order.

requested\_for
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The person for whom the shop articles are ordered. Defaults to the `requested_by`.

shop\_article
: *Readonly* **[string](../general/data_types.html)** containing `reference` field of [Shop Article](../shop_articles/index.html) — The shop article that was ordered.

shop\_article\_id
: *Required on create* **[integer](../general/data_types.html)** — The unique ID of the shop article that is being ordered.

source
: *Readonly* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Readonly* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

status
: *Readonly* **[enum](../general/enumerations/index.html)** — The status of the shop order line. Valid values are:
: - `in_cart`: In Cart
 - `workflow_pending`: Workflow Pending
 - `fulfillment_pending`: Fulfillment Pending
 - `completed`: Completed
 - `canceled`: Canceled

total\_price
: *Readonly* **[decimal](../general/data_types.html)** — The total (non-recurrent) price to be charged for all units combined.

total\_recurring\_price
: *Readonly* **[decimal](../general/data_types.html)** — The total yearly recurrent price to be charged for all units combined.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the shop order line. If the shop order line has no updates it contains the `created_at` value.
