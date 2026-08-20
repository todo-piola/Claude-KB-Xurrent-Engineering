# Service Instances - Child Service Instances API

## List child service instances of a service instance

List all [child service instances](../index.html) of the service instance with a specific ID.

```
GET /service_instances/:id/child_service_instances
```

### Response

```
status: 200 OK
```

```
[{"name":"Amsterdam Network","created_at":"2016-03-14T03:10:38-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:38-06:00","service":{"name":"Network Connectivity","id":20,"provider":{"name":"Widget Data Center, External IT","id":30}},"support_team":{"name":"Operations","id":11},"id":23,"status":"in_production"},{"name":"AT&T Smart Phone for Widget Data Center, External IT","created_at":"2016-03-14T03:10:39-06:00","sourceID":null,"updated_at":"2016-03-14T03:11:39-06:00","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"support_team":{"name":"End-User Support, Chicago","account":{"name":"Widget North America","id":"wna"},"id":16},"id":133,"status":"in_production"},"..."]
```

The response contains [these fields](../index.html#collection-fields) by default.
