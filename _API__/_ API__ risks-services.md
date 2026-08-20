# Risks - Services API

## List all services of a risk

List all [services](../../services.html) who are linked as a service to a risk with a specific ID.

```
GET /risks/:id/services
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

- `/risks/:id/services/disabled`: List all disabled services of a risk with a specific ID
- `/risks/:id/services/enabled`: List all enabled services of a risk with a specific ID

## Add a service to a risk

Add a link between a risk with a specific ID and a service with a specific ID.

```
POST /risks/:id/services/:service_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a service from a risk

Remove the link between a risk with a specific ID and a service with a specific ID.

```
DELETE /risks/:id/services/:service_id
```

### Response

```
status: 204 No Content
```

## Remove all services from a risk

Remove all links between a risk with a specific ID and its services.

```
DELETE /risks/:id/services
```

### Response

```
status: 204 No Content
```
