# Knowledge Articles - Requests API

## List requests of a knowledge article

List all [requests](../../requests.html) to which the knowledge article with a specific ID is linked.

```
GET /knowledge_articles/:id/requests
```

### Response

```
status: 200 OK
```

```
[{"service_instance":{"name":"Windows for Sales Tracking Production","id":126},"completed_at":null,"created_at":"2016-03-14T02:56:11-06:00","category":"rfc","sourceID":null,"updated_at":"2016-03-14T03:14:11-06:00","grouped_into":null,"member":{"name":"Barney Turban","id":58},"subject":"Add memory to Sales Tracking production server cluster","id":70470,"impact":null,"team":{"name":"Windows Servers","id":14},"status":"assigned","next_target_at":"best_effort"},"..."]
```

The response contains [these fields](../../requests.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/knowledge_articles/:id/requests/completed`: List all completed requests of a knowledge article with a specific ID
- `/knowledge_articles/:id/requests/open`: List all open requests of a knowledge article with a specific ID
