# People - Service Coverages API

## List service coverages of a person

List all [services](../../services.html) for which a [service instance](../../service_instances/index.html) exists for which a person with a specific ID is covered by an [SLA](../../service_level_agreements.html).

```
GET /people/:id/service_coverages
```

### Response

```
status: 200 OK
```

```
[{"name":"Conference Room","created_at":"2016-03-14T03:10:37-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:37-06:00","support_team":{"name":"End-User Support, Houston","id":9},"id":10,"disabled":false,"provider":{"name":"Widget Data Center, Internal IT","id":32}},{"name":"Customer Relationship Management (Siebel)","created_at":"2016-03-14T03:10:37-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:37-06:00","support_team":{"name":"Application Development","id":7},"id":11,"disabled":false,"provider":{"name":"Widget Data Center, External IT","id":30}},"..."]
```

The response contains [these fields](../../services.html#collection-fields) by default.
