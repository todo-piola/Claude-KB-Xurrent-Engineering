# Reservation Offerings - Request Templates API

## List request templates of a reservation offering

List all [request templates](../../request_templates.html) of the reservation offering with a specific ID.

```
GET /reservation_offerings/:id/request_templates
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:13:49-06:00","category":"rfi","sourceID":null,"updated_at":"2016-03-14T03:13:49-06:00","service":{"name":"Warehouse Management","id":32,"provider":{"name":"Widget Data Center, External IT","id":30}},"subject":"Request for information concerning the Warehouse Management service","id":118,"impact":null,"disabled":false},"..."]
```

The response contains [these fields](../../request_templates.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/reservation_offerings/:id/request_templates/disabled`: List all disabled request templates of a reservation offering with a specific ID
- `/reservation_offerings/:id/request_templates/enabled`: List all enabled request templates of a reservation offering with a specific ID
