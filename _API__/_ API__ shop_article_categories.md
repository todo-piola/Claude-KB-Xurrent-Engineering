# Shop Article Categories API

- [List shop article categories](index.html#list-shop-article-categories)
- [Get a single shop article category](index.html#get-a-single-shop-article-category)
- [Create a shop article category](index.html#create-a-shop-article-category)
- [Update a shop article category](index.html#update-a-shop-article-category)
- [Fields](index.html#fields)

## List shop article categories

List all shop article categories for an account:

```
GET /shop_article_categories
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2024-01-06T17:00:00-06:00","id":3,"name":"Computers","source":null,"sourceID":null,"updated_at":"2024-01-06T17:00:00-06:00","nodeID":"..."},{"created_at":"2024-01-06T17:00:00-06:00","id":4,"name":"Desktops","source":null,"sourceID":null,"updated_at":"2024-01-06T17:00:00-06:00","nodeID":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of shop article categories.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/shop_article_categories/directory`: List all shop article categories registered in the directory account of the support domain account from which the data is requested
- `/shop_article_categories/support_domain`: List all shop article categories registered in the account from which the data is requested

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of shop article categories:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `created_at` `updated_at`

### Sorting

By default a collection of shop article categories is sorted **ascending** by `created_at`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `source` `sourceID` `name` `created_at` `updated_at`

## Get a single shop article category

```
GET /shop_article_categories/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2024-01-06T17:00:00-06:00","full_description":"This category contains every computer imaginable provided by Widget Data Center. This is your one-stop shop for every device required to make your day productive.","id":3,"name":"Computers","picture_uri":"https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_categories/original/computers.svg","short_description":"All computers provided by Widget Data Center.","source":null,"sourceID":null,"updated_at":"2024-01-06T17:00:00-06:00","localized_full_description":"This category contains every computer imaginable provided by Widget Data Center. This is your one-stop shop for every device required to make your day productive.","localized_name":"Computers","localized_short_description":"All computers provided by Widget Data Center.","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Create a shop article category

```
POST /shop_article_categories
```

When creating a new shop article category [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created shop article category and is similar to the response in [Get a single shop article category](index.html#get-a-single-shop-article-category)

## Update a shop article category

```
PATCH /shop_article_categories/:id
```

When updating a shop article category [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated shop article category and is similar to the response in [Get a single shop article category](index.html#get-a-single-shop-article-category)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the shop article category was created.

full\_description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Full description field is used to enter a description of the shop article category.

full\_description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Full description field.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the shop article category.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the shop article category.

parent
: *Optional* **[reference](../general/data_types.html#references) to [Shop Article Category](index.html)** — The parent category.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the shop article category. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

short\_description
: *Optional* **[string](../general/data_types.html) (max 200)** — The Short description field is used to enter the a plain text short description to promote the shop article category.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the shop article category. If the shop article category has no updates it contains the `created_at` value.

### Localized Fields

The following fields support [localization](https://developer.xurrent.com/v1/general/localization/): `name`, `short_description`, `full_description`
