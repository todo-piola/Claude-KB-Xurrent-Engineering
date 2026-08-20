# Configuration Items - Requests API

## List all requests of a configuration item

List all [requests](../../requests.html) of the configuration item with a specific ID.

```
GET /cis/:id/requests
```

### Response

```
status: 200 OK
```

```
[{"service_instance":{"name":"Windows for Sales Tracking Production","id":126},"completed_at":null,"created_at":"2016-03-14T02:56:11-06:00","category":"rfc","sourceID":null,"updated_at":"2016-03-14T03:14:11-06:00","grouped_into":null,"member":{"name":"Barney Turban","id":58},"subject":"Add memory to Sales Tracking production server cluster","id":70470,"impact":null,"team":{"name":"Windows Servers","id":14},"status":"assigned","next_target_at":"best_effort"},"..."]
```

The response contains [these fields](../../requests.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/cis/:id/requests/completed`: List all completed requests of a configuration item with a specific ID
- `/cis/:id/requests/open`: List all open requests of a configuration item with a specific ID
