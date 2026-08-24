# Knowledge Article Templates - Knowledge Articles API

## List knowledge articles of a knowledge article template

List all [knowledge\_articles](../../knowledge_articles.html) to which the knowledge article template with a specific ID is linked.

```
GET /knowledge_article_templates/:id/knowledge_articles
```

### Response

```
status: 200 OK
```

```
[{"id":76,"sourceID":null,"subject":"How to connect a 2nd monitor to a desktop PC","status":"not_validated","service":{"id":31,"name":"Personal Computing","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Personal Computing"},"created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T14:10:05-06:00"},{"id":57,"sourceID":null,"subject":"How to book a conference room","status":"validated","key_contacts":true,"end_users":true,"service":{"id":18,"name":"Conference Room","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Conference Room"},"created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T02:16:24-06:00"},"..."]
```

The response contains [these fields](../../knowledge_articles.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/knowledge_article_templates/:id/knowledge_articles/active`: List all active knowledge articles of a knowledge article template with a specific ID
- `/knowledge_article_templates/:id/knowledge_articles/archived`: List all archived knowledge articles of a knowledge article template with a specific ID
- `/knowledge_article_templates/:id/knowledge_articles/managed_by_me`: List all knowledge articles that are linked to a service for which the API user is the knowledge manager of a knowledge article template with a specific ID
