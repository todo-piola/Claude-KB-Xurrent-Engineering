# Requests - Knowledge Articles API

## List all knowledge articles of a request

List all [knowledge articles](../../knowledge_articles.html) of a request with a specific ID.

```
GET /requests/:id/knowledge_articles
```

### Response

```
status: 200 OK
```

```
[{"id":76,"sourceID":null,"subject":"How to connect a 2nd monitor to a desktop PC","status":"not_validated","service":{"id":31,"name":"Personal Computing","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Personal Computing"},"created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T14:10:05-06:00"},{"id":57,"sourceID":null,"subject":"How to book a conference room","status":"validated","key_contacts":true,"end_users":true,"service":{"id":18,"name":"Conference Room","provider":{"id":46,"name":"Widget Data Center","account":{"id":"widget","name":"Widget International"}},"localized_name":"Conference Room"},"created_at":"2016-11-25T02:16:24-06:00","updated_at":"2016-11-25T02:16:24-06:00"},"..."]
```

The response contains [these fields](../../knowledge_articles.html#collection-fields) by default.
