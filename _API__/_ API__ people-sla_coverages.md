# People - SLA coverages API

## List SLA coverages of a person

List all [SLAs](../../service_level_agreements.html) by which a person with a specific ID is covered

```
GET /people/:id/sla_coverages
```

### Response

```
status: 200 OK
```

```
[{"name":"BlackBerry Standard Smart Phone for Widget Data Center, External IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":145,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},{"name":"BlackBerry Standard Smart Phone for Widget Data Center, Internal IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":146,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},"..."]
```

The response contains [these fields](../../service_level_agreements.html#collection-fields) by default.
