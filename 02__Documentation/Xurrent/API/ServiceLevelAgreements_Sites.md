# Service Level Agreements - Sites API

This API only works for service level agreements whose [Coverage](../../service_level_agreements.html#fields) field value is set to `sites` or `organizations_and_sites`.

## List all sites of a service level agreement

List all [sites](../../sites.html) of a service level agreement with a specific ID.

```
GET /slas/:id/sites
```

### Response

```
status: 200 OK
```

```
[{"name":"Widget Data Center","created_at":"2016-03-14T03:09:52-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:52-06:00","id":13},{"name":"IT Training Facility","created_at":"2016-03-14T09:10:17-06:00","sourceID":null,"updated_at":"2014-01-18T11:29:02-06:00","id":29,"disabled":true},"..."]
```

The response contains [these fields](../../sites.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/slas/:id/sites/disabled`: List all disabled sites of a service level agreement with a specific ID
- `/slas/:id/sites/enabled`: List all enabled sites of a service level agreement with a specific ID

## Add a site to a service level agreement

Add a link between a service level agreement with a specific ID and a site with a specific ID.

```
POST /slas/:id/sites/:site_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a site from a service level agreement

Remove the link between a service level agreement with a specific ID and a site with a specific ID.

```
DELETE /slas/:id/sites/:site_id
```

### Response

```
status: 204 No Content
```

## Remove all sites from a service level agreement

Remove all links between a service level agreement with a specific ID and its sites.

```
DELETE /slas/:id/sites
```

### Response

```
status: 204 No Content
```
