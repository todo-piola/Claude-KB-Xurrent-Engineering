# Services - Risks API

## List risks of a service

List all [risks](../../risks.html) of a service with a specific ID

```
GET /services/:id/risks
```

### Response

```
status: 200 OK
```

```
[{"id":12348,"sourceID":null,"subject":"Integration with cloud application could lead to breach of our Data Protection Policy","severity":"high","status":"closed","closed_at":"2020-01-15T09:55:00-06:00","closure_reason":"transferred","created_at":"2020-01-10T07:36:00-06:00","updated_at":"2020-02-11T05:30:55-06:00"},"..."]
```

The response contains [these fields](../../risks.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/services/:id/risks/open`: List all open risks of a service with a specific ID
- `/services/:id/risks/closed`: List all closed risks of a service with a specific ID
