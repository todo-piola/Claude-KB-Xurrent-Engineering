# Requests - Configuration Items API

## List all configuration items of a request

List all [configuration items](../../configuration_items/index.html) of a request with a specific ID.

```
GET /requests/:id/cis
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

- `/requests/:id/cis/active`: List all active configuration items of a request with a specific ID
- `/requests/:id/cis/inactive`: List all inactive configuration items of a request with a specific ID

## Add a configuration item to a request

Add a link between a request with a specific ID and a configuration item with a specific ID.

```
POST /requests/:id/cis/:ci_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a configuration item from a request

Remove the link between a request with a specific ID and a configuration item with a specific ID.

```
DELETE /requests/:id/cis/:ci_id
```

### Response

```
status: 204 No Content
```

## Remove all configuration items from a request

Remove all links between a request with a specific ID and its configuration items.

```
DELETE /requests/:id/cis
```

### Response

```
status: 204 No Content
```
