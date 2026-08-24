# Task Templates - Configuration Items API

## List all configuration items of a task template

List all [configuration items](../../configuration_items/index.html) of a task template with a specific ID.

```
GET /task_templates/:id/cis
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

- `/task_templates/:id/cis/active`: List all active configuration items of a task template with a specific ID
- `/task_templates/:id/cis/inactive`: List all inactive configuration items of a task template with a specific ID

## Add a configuration item to a task template

Add a link between a task template with a specific ID and a configuration item with a specific ID.

```
POST /task_templates/:id/cis/:ci_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a configuration item from a task template

Remove the link between a task template with a specific ID and a configuration item with a specific ID.

```
DELETE /task_templates/:id/cis/:ci_id
```

### Response

```
status: 204 No Content
```

## Remove all configuration items from a task template

Remove all links between a task template with a specific ID and its configuration items.

```
DELETE /task_templates/:id/cis
```

### Response

```
status: 204 No Content
```
