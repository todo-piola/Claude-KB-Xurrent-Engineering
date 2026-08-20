# Knowledge Articles API

- [List knowledge articles](../knowledge_articles.html#list-knowledge-articles)
- [Get a single knowledge article](../knowledge_articles.html#get-a-single-knowledge-article)
- [Create a knowledge article](../knowledge_articles.html#create-a-knowledge-article)
- [Update a knowledge article](../knowledge_articles.html#update-a-knowledge-article)
- [Fields](../knowledge_articles.html#fields)

## List knowledge articles

List all knowledge articles for an account:

```
GET /knowledge_articles
```

### Response

```
status: 200 OK
```

```
[{"id":76,"sourceID":null,"subject":"How to connect a 2nd monitor to a desktop PC","status":"not_validated","service":{"id":31,"name":"Personal Computing","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Personal Computing"},"created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T14:10:05-06:00"},{"id":57,"sourceID":null,"subject":"How to book a conference room","status":"validated","key_contacts":true,"end_users":true,"service":{"id":18,"name":"Conference Room","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Conference Room"},"created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T02:16:24-06:00"},"..."]
```

The response contains [these fields](../knowledge_articles.html#collection-fields) by default. [Filtering](../knowledge_articles.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of knowledge articles.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/knowledge_articles/active`: List all active knowledge articles
- `/knowledge_articles/archived`: List all archived knowledge articles
- `/knowledge_articles/managed_by_me`: List all knowledge articles that are linked to a service for which the API user is the knowledge manager

### Collection Fields

By default the following [fields](../knowledge_articles.html#fields) will appear in collections of knowledge articles:

`id` `sourceID` `subject` `status` `service` `created_at` `updated_at`

Obtain a different set of [fields](../knowledge_articles.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../knowledge_articles.html#fields):

`id` `source` `sourceID` `subject` `status` `service` `created_by` `created_at` `updated_at`

### Sorting

By default a collection of knowledge articles is sorted **descending** by `start_at`.

The following [fields](../knowledge_articles.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `status` `created_at` `updated_at`

### Response

The response is similar to the response in [List knowledge articles](../knowledge_articles.html#list-knowledge-articles)

## Get a single knowledge article

```
GET /knowledge_articles/:id
```

### Response

```
status: 200 OK
```

```
{"id":57,"locale":"en-US","subject":"How to book a conference room","keywords":"boardroom,meeting,appointment","description":"This article describes how you can book a conference room using Outlook.","instructions":"To book a conference room, follow the step below...","created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T02:16:24-06:00","source":null,"sourceID":null,"status":"validated","key_contacts":true,"end_users":true,"service":{"id":18,"name":"Conference Room","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Conference Room"}}
```

The response contains [these fields](../knowledge_articles.html#fields).

## Create a knowledge article

```
POST /knowledge_articles
```

When creating a new knowledge article [these fields](../knowledge_articles.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"instructions":"...","...":"..."}
```

The response contains [all fields](../knowledge_articles.html#fields) of the created knowledge article and is similar to the response in [Get a single knowledge article](../knowledge_articles.html#get-a-single-knowledge-article)

## Update a knowledge article

```
PATCH /knowledge_articles/:id
```

When updating a knowledge article [these fields](../knowledge_articles.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"instructions":"...","...":"..."}
```

The response contains [all fields](../knowledge_articles.html#fields) of the updated knowledge article and is similar to the response in [Get a single knowledge article](../knowledge_articles.html#get-a-single-knowledge-article)

## Fields

archive\_date
: *Optional* **[date](../general/data_types.html)** — The date until which the knowledge article will be active. The knowledge article will be archived at the beginning of this day. When the knowledge article is archived, its status will automatically be set to “Archived”.

attachments
: *Readonly* **aggregated Attachments**

covered\_specialists
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Covered specialists box is checked when the knowledge article needs to be available to the people who are a member of the support team of one of the service instances that are selected in the Coverage section of an active SLA for the service that is linked to the article.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the knowledge article was created.

created\_by
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Created by field is automatically set to the person who created the knowledge article.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the related knowledge article template.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

description
: *Required* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to describe the situation and/or environment in which the instructions of the knowledge article may be helpful.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

end\_users
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The End users box is checked when the knowledge article needs to be available to anyone who is covered by an active SLA for the service that is linked to the article.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the knowledge article.

instructions
: *Required* **[text](../general/data_types.html) (max 64KB)** — The Instructions field is used to enter instructions for the service desk analysts, specialists and/or end users who are likely to look up the knowledge article to help them with their work or to resolve an issue.

instructions\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Instructions field.

internal\_specialists
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Internal specialists box is checked when the knowledge article needs to be available to the people who have the Specialist role of the account in which the article is registered.

key\_contacts
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Key contacts box is checked when the knowledge article needs to be available to the people who have the Key Contact role of the customer account of an active SLA for the service that is linked to the article.

keywords
: *Optional* **[string](../general/data_types.html) (max 2048)** — The Keywords field contains a comma-separated list of words that can be used to find the knowledge article using search.

locale
: *Optional* **[string](../general/data_types.html) (max 5)** — The language of the knowledge article.

service
: *Required* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the [service](../services.html) for which the knowledge article is made available.

source
: *Optional* **[string](../general/data_types.html) (max 30)** — See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** — See [source](../general/source.html)

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `not_validated` — The Status field is used to select the current status of the knowledge article. Valid values are:
: - `work_in_progress`: Work In Progress
 - `not_validated`: Not Validated
 - `validated`: Validated
 - `archived`: Archived

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the knowledge article.

template
: *Optional* **[reference](../general/data_types.html#references) to [Knowledge Article Template](../knowledge_article_templates/index.html)** — The Template field is used to select the [knowledge article template](../knowledge_article_templates/index.html) on which the knowledge article is based.

times\_applied
: *Readonly* **[integer](../general/data_types.html)** — The number of requests to which the knowledge article is linked as the last applied knowledge article.

times\_viewed
: *Readonly* **[integer](../general/data_types.html)** — The all-time total of self-service views of the knowledge article.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the knowledge article. If the knowledge article has no updates it contains the `created_at` value.

updated\_by
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Updated by field is automatically set to the person who last updated the knowledge article. If the knowledge article has no updates it contains the `created_by` value.
