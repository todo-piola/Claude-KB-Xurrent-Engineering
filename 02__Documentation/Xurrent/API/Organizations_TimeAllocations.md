# Organizations - Time Allocations API

## List all time allocations of an organization

List all [time allocations](../../time_allocations/index.html) of an organization with a specific ID.

```
GET /organizations/:id/time_allocations
```

### Response

```
status: 200 OK
```

```
[{"id":4,"sourceID":null,"name":"Transparency of Performance (TOP)","group":"Project","created_at":"2016-03-22T21:03:35-05:00","updated_at":"2016-03-22T21:03:35-05:00","localized_group":"Project","localized_name":"Transparency of Performance (TOP)"},{"id":12,"sourceID":null,"name":"Warehouse Ordering (WHO)","group":"Project","created_at":"2016-03-22T21:03:36-05:00","updated_at":"2016-03-22T21:03:36-05:00","disabled":true,"localized_group":"Project","localized_name":"Warehouse Ordering (WHO)"},"..."]
```

The response contains [these fields](../../time_allocations/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/organizations/:id/time_allocations/disabled`: List all disabled time allocations of an organization with a specific ID
- `/organizations/:id/time_allocations/enabled`: List all enabled time allocations of an organization with a specific ID

## Add a time allocation to an organization

Add a link between an organization with a specific ID and a time allocation with a specific ID.

```
POST /organizations/:id/time_allocations/:time_allocation_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a time allocation from an organization

Remove the link between an organization with a specific ID and a time allocation with a specific ID.

```
DELETE /organizations/:id/time_allocations/:time_allocation_id
```

### Response

```
status: 204 No Content
```

## Remove all time allocations from an organization

Remove all links between an organization with a specific ID and its time allocations.

```
DELETE /organizations/:id/time_allocations
```

### Response

```
status: 204 No Content
```
