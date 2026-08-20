# SLA Coverage Groups - Service Level Agreements API

- [List all service level agreements of an SLA coverage group](index.html#list-all-service-level-agreements-of-an-sla-coverage-group)
- [Add a service level agreement to an SLA coverage group](index.html#add-a-service-level-agreement-to-an-sla-coverage-group)
- [Remove a service level agreement from an SLA coverage group](index.html#remove-a-service-level-agreement-from-an-sla-coverage-group)
- [Remove all service level agreements from an SLA coverage group](index.html#remove-all-service-level-agreements-from-an-sla-coverage-group)

## List all service level agreements of an SLA coverage group

List all [service level agreements](../../service_level_agreements.html) of the SLA coverage group with a specific ID.

```
GET /sla_coverage_groups/:id/slas
```

### Response

```
status: 200 OK
```

```
[{"name":"BlackBerry Standard Smart Phone for Widget Data Center, External IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":145,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},{"name":"BlackBerry Standard Smart Phone for Widget Data Center, Internal IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":146,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},"..."]
```

The response contains [these fields](../../service_level_agreements.html#collection-fields) by default.

## Add a service level agreement to an SLA coverage group

Add a link between an SLA coverage group with a specific ID and a service level agreement with a specific ID.

```
POST /sla_coverage_groups/:id/slas/:sla_id
```

### Response

```
status: 200 OK
```

## Remove a service level agreement from an SLA coverage group

Remove the link between an SLA coverage group with a specific ID and a service level agreement with a specific ID.

```
DELETE /sla_coverage_groups/:id/slas/:sla_id
```

### Response

```
status: 204 No Content
```

## Remove all service level agreements from an SLA coverage group

Remove all service level agreement links from an SLA coverage group with a specific ID.

```
DELETE /sla_coverage_groups/:id/slas
```

### Response

```
status: 204 No Content
```
