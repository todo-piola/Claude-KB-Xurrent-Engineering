# Reservation Offerings - Configuration Items API

## List configuration items of a reservation offerings

List all [configuration items](../../configuration_items/index.html) of the reservation offering with with a specific ID.

```
GET /reservation_offerings/:id/cis
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

- `/reservation_offerings/:id/cis/active`: List all active configuration items of a reservation offering with a specific ID
- `/reservation_offerings/:id/cis/inactive`: List all inactive configuration items of a reservation offering with a specific ID
