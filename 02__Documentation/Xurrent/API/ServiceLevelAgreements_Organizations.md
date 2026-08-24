# Service Level Agreements - Organizations API

This API works only for service level agreements which [Coverage](../../service_level_agreements.html#fields) field value is set to `organizations_and_descendants`, `organizations` or `organizations_and_sites`.

## List all organizations of a service level agreement

List all [organizations](../../organizations.html) of a service level agreement with a specific ID.

```
GET /slas/:id/organizations
```

### Response

```
status: 200 OK
```

```
[{"id":44,"sourceID":null,"name":"Widget Data Center, External IT","parent":{"id":6,"name":"Widget Data Center"},"manager":{"id":6,"name":"Howard Tanner"},"created_at":"2016-03-22T21:02:50-05:00","updated_at":"2016-03-25T16:54:52-05:00"},{"id":50,"sourceID":null,"name":"Widget North America, Finance","parent":{"id":51,"name":"Widget North America, Inc."},"manager":{"id":120,"name":"Carolyn Goldrat"},"created_at":"2016-03-22T21:02:50-05:00","updated_at":"2016-03-22T21:03:36-05:00"},"..."]
```

The response contains [these fields](../../organizations.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/slas/:id/organizations/disabled`: List all disabled organizations of a service level agreement with a specific ID
- `/slas/:id/organizations/enabled`: List all enabled organizations of a service level agreement with a specific ID
- `/slas/:id/organizations/external`: List all external organizations of a service level agreement with a specific ID
- `/slas/:id/organizations/internal`: List all internal organizations of a service level agreement with a specific ID

## Add an organization to a service level agreement

Add a link between a service level agreement with a specific ID and an organization with a specific ID.

```
POST /slas/:id/organizations/:organization_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove an organization from a service level agreement

Remove the link between a service level agreement with a specific ID and an organization with a specific ID.

```
DELETE /slas/:id/organizations/:organization_id
```

### Response

```
status: 204 No Content
```

## Remove all organizations from a service level agreement

Remove all links between a service level agreement with a specific ID and its organizations.

```
DELETE /slas/:id/organizations
```

### Response

```
status: 204 No Content
```
