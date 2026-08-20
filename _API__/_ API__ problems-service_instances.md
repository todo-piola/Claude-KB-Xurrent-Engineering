# Problems - Service Instances API

## List all service instances of a problem

List all [service instances](../../service_instances/index.html) of a problem with a specific ID.

```
GET /problems/:id/service_instances
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

- `/problems/:id/service_instances/active`: List all active service instances of a problem with a specific ID
- `/problems/:id/service_instances/inactive`: List all inactive service instances of a problem with a specific ID

## Add a service instance to a problem

Add a link between a problem with a specific ID and a service instance with a specific ID.

```
POST /problems/:id/service_instances/:service_instance_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a service instance from a problem

Remove the link between a problem with a specific ID and a service instance with a specific ID.

```
DELETE /problems/:id/service_instances/:service_instance_id
```

### Response

```
status: 204 No Content
```

## Remove all service instances from a problem

Remove all links between a problem with a specific ID and its service instances.

```
DELETE /problems/:id/service_instances
```

### Response

```
status: 204 No Content
```
