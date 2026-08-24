# Services - Service Instances API

## List service instances of a service

List all [service instances](../../service_instances/index.html) of the service with a specific ID.

```
GET /services/:id/service_instances
```

### Response

```
status: 200 OK
```

```
[{"name":"Amsterdam Network","created_at":"2016-03-14T03:10:38-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:38-06:00","service":{"name":"Network Connectivity","id":20,"provider":{"name":"Widget Data Center, External IT","id":30}},"support_team":{"name":"Operations","id":11},"id":23,"status":"in_production"},{"name":"AT&T Smart Phone for Widget Data Center, External IT","created_at":"2016-03-14T03:10:39-06:00","sourceID":null,"updated_at":"2016-03-14T03:11:39-06:00","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"support_team":{"name":"End-User Support, Chicago","account":{"name":"Widget North America","id":"wna"},"id":16},"id":133,"status":"in_production"},"..."]
```

The response contains [these fields](../../service_instances/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/services/:id/service_instances/active`: List all active service instances of a service with a specific ID
- `/services/:id/service_instances/inactive`: List all inactive service instances of a service with a specific ID
