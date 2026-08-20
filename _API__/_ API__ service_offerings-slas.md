# Service Offerings - Service Level Agreements API

## List service level agreements of a service offering

List all [service level agreements](../../service_level_agreements.html) of the service offering with a specific ID.

```
GET /service_offerings/:id/slas
```

### Response

```
status: 200 OK
```

```
[{"name":"BlackBerry Standard Smart Phone for Widget Data Center, External IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":145,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},{"name":"BlackBerry Standard Smart Phone for Widget Data Center, Internal IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":146,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},"..."]
```

The response contains [these fields](../../service_level_agreements.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/service_offerings/:id/slas/active`: List all active service level agreements of a service offering with a specific ID
- `/service_offerings/:id/slas/inactive`: List all inactive service level agreements of a service offering with a specific ID
