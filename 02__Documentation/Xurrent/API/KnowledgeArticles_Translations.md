# Knowledge Article Translations API

- [List knowledge article translations](index.html#list-knowledge-article-translations)
- [Get a single knowledge article translation](index.html#get-a-single-knowledge-article-translation)
- [Fields](index.html#fields)

## List knowledge article translations

List all knowledge article translations for a Knowledge Article:

```
GET /knowledge_articles/:knowledge_article_id/translations
```

### Response

```
status: 200 OK
```

```
[{"id":81,"locale":"de","created_at":"2016-05-23T09:35:52-05:00","updated_at":"2016-05-23T09:35:52-05:00"},{"id":63,"locale":"en-US","created_at":"2016-05-22T03:20:36-05:00","updated_at":"2016-05-26T06:13:56-05:00"},"..."]
```

The response contains [these fields](index.html#collection-fields).

### Collection Fields

The following [fields](index.html#fields) will appear in collections of knowledge article translations:

- `id`
- `locale`
- `created_at`
- `updated_at`

### Sorting

A collection of knowledge article translations is sorted **descending** by `created_at`.

## Get a single knowledge article translation

```
GET /knowledge_articles/:knowledge_article_id/translations/:id
```

### Response

```
status: 200 OK
```

```
{"id":63,"locale":"en-US","subject":"How to book a conference room","description":"This article describes how you can book a conference room using Outlook.","instructions":"To book a conference room, follow the step below...","created_at":"2016-05-22T03:20:36-05:00","updated_at":"2016-05-26T06:13:56-05:00"}
```

The response contains [these fields](index.html#fields).

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the knowledge article translation was created.

description
: *Required* **[text](../../general/data_types.html) (max 64KB)** — The Description field is used to describe the situation and/or environment in which the instructions of the knowledge article may be helpful in the language of the locale.

description\_attachments
: *Writeonly* **[attachments](../../general/data_types.html#attachments)** The attachments used in the Description field.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the knowledge article translation.

instructions
: *Required* **[text](../../general/data_types.html) (max 64KB)** — The Instructions field is used to enter instructions in the language of the locale for the service desk analysts, specialists and/or end users who are likely to look up the knowledge article to help them with their work or to resolve an issue.

instructions\_attachments
: *Writeonly* **[attachments](../../general/data_types.html#attachments)** The attachments used in the Instructions field.

locale
: *Optional* **[string](../../general/data_types.html) (max 5)**

subject
: *Required* **[string](../../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the knowledge article in the language of the locale.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the knowledge article translation. If the knowledge article translation has no updates it contains the `created_at` value.
