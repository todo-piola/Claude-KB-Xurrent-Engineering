# Service Level Agreements - Service Instances API

- [List all parent service instances of a service level agreement](index.html#list-all-parent-service-instances-of-a-service-level-agreement)
- [Add a parent service instance to a service level agreement](index.html#add-a-parent-service-instance-to-a-service-level-agreement)
- [Update a parent service instance of a service level agreement](index.html#update-a-parent-service-instance-of-a-service-level-agreement)
- [Remove a parent service instance from a service level agreement](index.html#remove-a-parent-service-instance-from-a-service-level-agreement)
- [Remove all parent service instances from a service level agreement](index.html#remove-all-parent-service-instances-from-a-service-level-agreement)
- [Fields](../../parent_service_instances/index.html#collection-fields)

## List all parent service instances of a service level agreement

List all [parent service instances](../../parent_service_instances/index.html) of the service level agreement with a specific ID:

```
GET /slas/:id/service_instances
```

### Response

```
status: 200 OK
```

```
[{"id":"4558","service_instance":{"name":"Rack Space","id":339},"impact_relation":"degraded"},{"id":324,"service_instance":{"name":"Premium Rack Space","id":340},"impact_relation":"down"}]
```

The response contains [these fields](../../parent_service_instances/index.html#collection-fields) by default.

## Add a parent service instance to a service level agreement

Add a Service Instance to a service level agreement with a specific ID.

```
POST /slas/:id/service_instances
```

When creating a new Service Instance for a service level agreement [these fields](../../parent_service_instances/index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"4558","service_instance":{"name":"Rack Space","id":339},"impact_relation":"degraded"}
```

## Update a parent service instance of a service level agreement

Update a Service Instance with a specific ID of a service level agreement with a specific ID.

```
PATCH /slas/:id/service_instances/:parent_service_instance_id
```

When updating an existing parent service instance for a service level agreement [these fields](../../parent_service_instances/index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"impact_relation":"down","...":"..."}
```

## Remove a parent service instance from a service level agreement

Remove a parent service instance with a specific ID link from a service level agreement with a specific ID.

```
DELETE /slas/:id/service_instances/:parent_service_instance_id
```

### Response

```
status: 204 No Content
```

## Remove all parent service instances from a service level agreement

Remove all parent service instances from a service level agreement with a specific ID.

```
DELETE /slas/:id/service_instances/
```

### Response

```
status: 204 No Content
```
