# Service Categories - Services API

## List all services of a service category

List all [services](../../services.html) of a service category with a specific ID.

```
GET /service_categories/:id/services
```

### Response

```
status: 200 OK
```

```
[{"name":"Conference Room","created_at":"2016-03-14T03:10:37-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:37-06:00","support_team":{"name":"End-User Support, Houston","id":9},"id":10,"disabled":false,"provider":{"name":"Widget Data Center, Internal IT","id":32}},{"name":"Customer Relationship Management (Siebel)","created_at":"2016-03-14T03:10:37-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:37-06:00","support_team":{"name":"Application Development","id":7},"id":11,"disabled":false,"provider":{"name":"Widget Data Center, External IT","id":30}},"..."]
```

The response contains [these fields](../../services.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/service_categories/:id/services/disabled`: List all disabled services of a service category with a specific ID
- `/service_categories/:id/services/enabled`: List all enabled services of a service category with a specific ID

## Add a service to a service category

Add a link between a service category with a specific ID and a service with a specific ID.

```
POST /service_categories/:id/services/:service_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a service from a service category

Remove the link between a service category with a specific ID and a service with a specific ID.

```
DELETE /service_categories/:id/services/:service_id
```

### Response

```
status: 204 No Content
```

## Remove all services from a service category

Remove all links between a service category with a specific ID and its services.

```
DELETE /service_categories/:id/services
```

### Response

```
status: 204 No Content
```
