# Invoices - Configuration Items API

## List all configuration items linked to an invoice

List all [configuration items](../../configuration_items/index.html) that are linked to an invoice with a specific ID.

```
GET /invoices/:id/cis
```

### Response

```
status: 200 OK
```

```
[{"name":"Adobe Reader 9.1.0","label":"Adobe Reader 9.1.0","created_at":"2016-03-14T03:11:22-06:00","sourceID":null,"updated_at":"2016-03-14T03:11:22-06:00","service":{"name":"Personal Computing","id":22,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"support_team":{"name":"End-User Support, Houston","id":9},"id":711,"product":{"name":"Adobe Reader","brand":"Adobe","category":"software/browser_viewer_application","id":33},"status":"in_production","software":true,"rule_set":"software"},"..."]
```

The response contains [these fields](../../configuration_items/index.html#collection-fields) by default.

## Add a configuration item to an invoice

Add a link between an invoice with a specific ID and a configuration item with a specific ID.

```
POST /invoices/:id/cis/:ci_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a configuration item from an invoice

Remove the link between an invoice with a specific ID and a configuration item with a specific ID.

```
DELETE /invoices/:id/cis/:ci_id
```

### Response

```
status: 204 No Content
```
