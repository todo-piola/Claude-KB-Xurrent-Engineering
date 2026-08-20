# Time Allocations - Services API

## List all services of a time allocation

List all [services](../../services.html) of a time allocation with a specific ID.

```
GET /time_allocations/:id/services
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

- `/time_allocations/:id/services/disabled`: List all disabled services of a time allocation with a specific ID
- `/time_allocations/:id/services/enabled`: List all enabled services of a time allocation with a specific ID

## Add a service to a time allocation

Add a link between a time allocation with a specific ID and a service with a specific ID.

```
POST /time_allocations/:id/services/:service_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a service from a time allocation

Remove the link between a time allocation with a specific ID and a service with a specific ID.

```
DELETE /time_allocations/:id/services/:service_id
```

### Response

```
status: 204 No Content
```

## Remove all services from a time allocation

Remove all links between a time allocation with a specific ID and its services.

```
DELETE /time_allocations/:id/services
```

### Response

```
status: 204 No Content
```
