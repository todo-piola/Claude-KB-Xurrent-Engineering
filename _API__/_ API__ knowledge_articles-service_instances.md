# Knowledge Articles - Service Instances API

## List service instances of a knowledge article

List all [service instances](../../service_instances/index.html) to which the knowledge article with a specific ID is linked.

```
GET /knowledge_articles/:id/service_instances
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

- `/knowledge_articles/:id/service_instances/active`: List all active service instances of a knowledge article with a specific ID
- `/knowledge_articles/:id/service_instances/inactive`: List all inactive service instances of a knowledge article with a specific ID

## Add a service instance to a knowledge article

Add a link between a knowledge article with a specific ID and a service instance with a specific ID.

```
POST /knowledge_articles/:id/service_instances/:service_instance_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a service instance from a knowledge article

Remove the link between a knowledge article with a specific ID and a service instance with a specific ID.

```
DELETE /knowledge_articles/:id/service_instances/:service_instance_id
```

### Response

```
status: 204 No Content
```

## Remove all service instances from a knowledge article

Remove all links between a knowledge article with a specific ID and its service instances.

```
DELETE /knowledge_articles/:id/service_instances
```

### Response

```
status: 204 No Content
```
