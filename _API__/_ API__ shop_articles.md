# Shop Articles API

- [List shop articles](index.html#list-shop-articles)
- [Get a single shop article](index.html#get-a-single-shop-article)
- [Create a shop article](index.html#create-a-shop-article)
- [Update a shop article](index.html#update-a-shop-article)
- [Fields](index.html#fields)

## List shop articles

List all shop articles for an account:

```
GET /shop_articles
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2022-11-24T08:11:21-06:00","id":2,"name":"Dell Precision M4400","reference":"dell_m4400","sourceID":null,"updated_at":"2022-11-24T08:11:21-06:00","nodeID":"..."},{"created_at":"2022-11-24T08:11:21-06:00","id":3,"name":"Dell Precision T5400 Workstation","reference":"dell_t5400","sourceID":null,"updated_at":"2022-11-24T08:11:21-06:00","nodeID":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of shop articles.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/shop_articles/enabled`: List all shop articles that are enabled
- `/shop_articles/disabled`: List all shop articles that are disabled
- `/shop_articles/on_offer`: List all shop articles with the information (name, pricing, etc.) as it is on offer in the shop

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of shop articles:

`id`, `sourceID`, `reference`, `name`, `created_at`, `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id`, `source`, `sourceID`, `reference`, `name`, `disabled`, `created_at`, `updated_at`

### Sorting

By default a collection of shop articles is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id`, `sourceID`, `reference`, `name`, `created_at`, `updated_at`

## Get a single shop article

```
GET /shop_articles/:id
```

### Response

```
status: 200 OK
```

```
{"calendar":{"id":50,"name":"24x7 (Monday through Sunday)","nodeID":"..."},"category":{"id":5,"name":"Laptops","localized_name":"Laptops","nodeID":"..."},"created_at":"2022-11-24T08:11:21-06:00","delivery_duration":8640,"disabled":false,"end_at":null,"fulfillment_template":{"id":1401,"subject":"Deliver Shop Article","localized_subject":"Deliver Shop Article","nodeID":"..."},"full_description":"Dell’s most powerful 17\" mobile workstation with AI. Featuring up to Intel® Core® or Xeon® processors, NVIDIA® professional graphics and Dell Optimizer for Precision.","id":2,"max_quantity":1,"name":"Dell Precision M4400","picture_uri":"https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_accounts/large/Dell Precision M4400 Laptop PC.png","price":"2350.0","price_currency":"usd","product":{"id":47,"name":"Dell Precision M4400 Laptop PC","category":"computer/laptop_pc","nodeID":"...","brand":"Dell EMC","model":"Precision M4400"},"recurring_period":null,"recurring_price":null,"recurring_price_currency":null,"reference":"DellM4400","requires_shipping":true,"short_description":"Dell’s most powerful 17\" mobile workstation with AI.","source":null,"sourceID":null,"start_at":null,"time_zone":"Central Time (US & Canada)","ui_extension":null,"updated_at":"2022-11-24T08:11:21-06:00","localized_full_description":"Dell’s most powerful 17\" mobile workstation with AI. Featuring up to Intel® Core® or Xeon® processors, NVIDIA® professional graphics and Dell Optimizer for Precision.","localized_name":"Dell Precision M4400","localized_short_description":"Dell’s most powerful 17\" mobile workstation with AI.","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Create a shop article

```
POST /shop_articles
```

When creating a new shop article [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created shop article and is similar to the response in [Get a single shop article](index.html#get-a-single-shop-article)

## Update a shop article

```
PATCH /shop_articles/:id
```

When updating a shop article [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated shop article and is similar to the response in [Get a single shop article](index.html#get-a-single-shop-article)

## Fields

attachments
: *Readonly* **aggregated Attachments**

calendar
: *Required* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Calendar field is used to select the [Calendar](../calendars/index.html) that defines the work hours related to the fulfillment/delivery.

category
: *Optional* **[reference](../general/data_types.html#references) to [Category](../shop_article_categories/index.html)** — The Category field can be used to relate the shop article to a category.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the shop article was created.

delivery\_duration
: *Required* **[integer](../general/data_types.html)** — The Delivery duration field is used to specify the time it takes to deliver the shop article.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the shop article is not visible in the shop.

end\_at
: *Optional* **[datetime](../general/data_types.html)** — The End field is used to select the end date and time at which the article needs to be disabled and thereby removed from the shop.

fulfillment\_template
: *Required* **[reference](../general/data_types.html#references) to [Request template](../request_templates.html)** — The fulfillment template related to the shop article. The request template is used to order one of more units of this shop article.

full\_description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Full description field is used to enter a description of the shop article.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the shop article.

is\_bundle
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Set to `true` to make the shop article a bundle composed of other shop articles. Can only be set when the shop article is created.

max\_quantity
: *Optional* **[integer](../general/data_types.html)**, default: `1` — The Quantity field is used to enter the maximum number of units that are allowed to be ordered in a single fulfillment request.

name
: *Required* **[string](../general/data_types.html) (max 64)** — The Name field is used to enter the name of the shop article.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the shop article. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

price
: *Optional* **[decimal](../general/data_types.html)** — The Price field is used to enter the amount to be charged per unit that was ordered.

price\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — The currency of the price.

product
: *Optional* **[reference](../general/data_types.html#references) to [Product](../products.html)** — The Product field can be used to relate the shop article to a product.

recurring\_period
: *Optional* **[enum](../general/enumerations/index.html)** — The Recurring period field is used to select the interval for a recurring price. Valid values are:
: - `monthly`: Monthly
 - `yearly`: Yearly

recurring\_price
: *Optional* **[decimal](../general/data_types.html)** — The Recurring price field is used to enter the amount to be charged recurrently per unit that was ordered.

recurring\_price\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — The currency of the recurrent price.

reference
: *Required* **[string](../general/data_types.html) (max 128)** — The Reference field can be used to identify the shop article. It must be unique within the account.

requires\_shipping
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Set to the value `true` if the shop articles requires shipping and therefore a shipping address must be present in the order.

short\_description
: *Optional* **[string](../general/data_types.html) (max 200)** — The Short description field is used to enter the a plain text short description to promote the shop article.

start\_at
: *Optional* **[datetime](../general/data_types.html)** — The Start field is used to select the start date and time at which the article needs to be enabled and thereby become visible in the shop.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

time\_zone
: *Required* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the selected calendar.

ui\_extension
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field is used to select the UI extension that is to be filled out before the shop article is added to the cart.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the shop article. If the shop article has no updates it contains the `created_at` value.
