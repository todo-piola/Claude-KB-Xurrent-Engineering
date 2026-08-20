# Knowledge Article Templates API

- [List knowledge article templates](index.html#list-knowledge-articles)
- [Get a single knowledge article template](index.html#get-a-single-knowledge-article-template)
- [Create a knowledge article template](index.html#create-a-knowledge-article-template)
- [Update a knowledge article template](index.html#update-a-knowledge-article-template)
- [Fields](index.html#fields)

## List knowledge article templates

List all knowledge article templates for an account:

```
GET /knowledge_article_templates
```

### Response

```
status: 200 OK
```

```
[{"id":76,"sourceID":null,"subject":"How to connect a 2nd monitor to a desktop PC","service":{"id":31,"name":"Personal Computing","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Personal Computing"},"created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T14:10:05-06:00"},{"id":57,"sourceID":null,"subject":"How to book a conference room","service":{"id":18,"name":"Conference Room","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Conference Room"},"created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T02:16:24-06:00"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of knowledge article templates.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/knowledge_article_templates/enabled`: List all enabled knowledge article templates
- `/knowledge_article_templates/disabled`: List all disabled knowledge article templates

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of knowledge article templates:

`id` `sourceID` `subject` `service` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `subject` `disabled` `service` `created_at` `updated_at`

### Sorting

By default a collection of knowledge article templates is sorted **descending** by `start_at`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `service` `created_at` `updated_at`

### Response

The response is similar to the response in [List knowledge article templates](index.html#list-knowledge-articles)

## Get a single knowledge article template

```
GET /knowledge_article_templates/:id
```

### Response

```
status: 200 OK
```

```
{"id":76,"sourceID":null,"subject":"How to connect a 2nd monitor to a desktop PC","service":{"id":31,"name":"Personal Computing","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Personal Computing"},"created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T14:10:05-06:00"}
```

The response contains [these fields](index.html#fields).

## Create a knowledge article template

```
POST /knowledge_article_templates
```

When creating a new knowledge article template [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"subject":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created knowledge article template and is similar to the response in [Get a single knowledge article template](index.html#get-a-single-knowledge-article-template)

## Update a knowledge article template

```
PATCH /knowledge_article_templates/:id
```

When updating a knowledge article template [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"subject":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated knowledge article template and is similar to the response in [Get a single knowledge article template](index.html#get-a-single-knowledge-article-template)

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the knowledge article template was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the knowledge article template may no longer be related to other records.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the knowledge article template.

service
: *Optional* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the [service](../services.html) for which the knowledge article template is made available.

source
: *Optional* **[string](../general/data_types.html) (max 30)** — See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** — See [source](../general/source.html)

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the knowledge article template.

ui\_extension
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field is used to select the UI extension that is to be added to the knowledge articles that are based on the template.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the knowledge article template. If the knowledge article template has no updates it contains the `created_at` value.
