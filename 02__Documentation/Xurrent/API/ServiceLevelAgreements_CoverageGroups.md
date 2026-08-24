# Service Level Agreements - Coverage Groups API

- [List all coverage groups of a service level agreement](index.html#list-all-coverage-groups-of-a-service-level-agreement)
- [Add a coverage group to a service level agreement](index.html#add-a-coverage-group-to-a-service-level-agreement)
- [Remove a coverage group from a service level agreement](index.html#remove-a-coverage-group-from-a-service-level-agreement)
- [Remove all coverage groups from a service level agreement](index.html#remove-all-coverage-groups-from-a-service-level-agreement)

## List all coverage groups of a service level agreement

List all [SLA coverage groups](../../sla_coverage_groups/index.html) of the service level agreement with a specific ID.

```
GET /slas/:id/coverage_groups
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2023-11-17T02:37:24-06:00","description":null,"disabled":false,"id":2,"name":"Beatrice","search_phrase":null,"source":"4me","sourceID":null,"updated_at":"2023-11-17T02:37:24-06:00","nodeID":"..."},{"created_at":"2023-11-17T02:41:10-06:00","description":null,"disabled":false,"id":3,"name":"Finance","search_phrase":"Finance","source":"4me","sourceID":null,"updated_at":"2023-11-17T02:41:10-06:00","nodeID":"..."},"..."]
```

The response contains [these fields](../../sla_coverage_groups/index.html#collection-fields) by default.

## Add a coverage group to a service level agreement

Add a link between a service level agreement with a specific ID and an SLA coverage group with a specific ID.

```
POST /slas/:id/coverage_groups/:coverage_group_id
```

### Response

```
status: 200 OK
```

## Remove a coverage group from a service level agreement

Remove the link between a service level agreement with a specific ID and an SLA coverage group with a specific ID.

```
DELETE /slas/:id/coverage_groups/:coverage_group_id
```

### Response

```
status: 204 No Content
```

## Remove all coverage groups from a service level agreement

Remove all SLA coverage group links from a service level agreement with a specific ID.

```
DELETE /slas/:id/coverage_groups
```

### Response

```
status: 204 No Content
```
