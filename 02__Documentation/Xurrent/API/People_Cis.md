# People - Configuration Items API

## List configuration items of a person

List all [configuration items](../../configuration_items/index.html) to which a person with a specific ID is related as a user.

```
GET /people/:id/cis
```

### Response

```
status: 200 OK
```

```
[{"name":"Adobe Reader 9.1.0","label":"Adobe Reader 9.1.0","created_at":"2016-03-14T03:11:22-06:00","sourceID":null,"updated_at":"2016-03-14T03:11:22-06:00","service":{"name":"Personal Computing","id":22,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"support_team":{"name":"End-User Support, Houston","id":9},"id":711,"product":{"name":"Adobe Reader","brand":"Adobe","category":"software/browser_viewer_application","id":33},"status":"in_production","software":true,"rule_set":"software"},"..."]
```

The response contains [these fields](../../configuration_items/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/people/:id/cis/active`: List all active configuration items of a person with a specific ID
- `/people/:id/cis/inactive`: List all inactive configuration items of a person with a specific ID

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](index.html#/v1/configuration_items/#fields):

`status` `rule_set`

## Add a configuration item to a person

Add a link between a person with a specific ID and a configuration item with a specific ID.

```
POST /people/:id/cis/:ci_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a configuration item from a person

Remove the link between a person with a specific ID and a configuration item with a specific ID.

```
DELETE /people/:id/cis/:ci_id
```

### Response

```
status: 204 No Content
```

## Remove all configuration items from a person

Remove all links between a person with a specific ID and its configuration items.

```
DELETE /people/:id/cis
```

### Response

```
status: 204 No Content
```
