# Services - Request Templates API

## List request templates of a service

List all [request templates](../../request_templates.html) of the service with a specific ID.

```
GET /services/:id/request_templates
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:13:49-06:00","category":"rfi","sourceID":null,"updated_at":"2016-03-14T03:13:49-06:00","service":{"name":"Warehouse Management","id":32,"provider":{"name":"Widget Data Center, External IT","id":30}},"subject":"Request for information concerning the Warehouse Management service","id":118,"impact":null,"disabled":false},"..."]
```

The response contains [these fields](../../request_templates.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/services/:id/request_templates/disabled`: List all disabled request templates of a service with a specific ID
- `/services/:id/request_templates/enabled`: List all enabled request templates of a service with a specific ID
