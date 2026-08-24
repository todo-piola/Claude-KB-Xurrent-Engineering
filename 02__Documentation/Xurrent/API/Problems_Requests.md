# Problems - Requests API

## List all requests of a problem

List all [requests](../../requests.html) of a problem with a specific ID.

```
GET /problems/:id/requests
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

- `/problems/:id/requests/completed`: List all completed requests of a problem with a specific ID
- `/problems/:id/requests/open`: List all open requests of a problem with a specific ID

## Add a request to a problem

Add a link between a problem with a specific ID and a request with a specific ID.

```
POST /problems/:id/requests/:request_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a request from a problem

Remove the link between a problem with a specific ID and a request with a specific ID.

```
DELETE /problems/:id/requests/:request_id
```

### Response

```
status: 204 No Content
```

## Remove all requests from a problem

Remove all links between a problem with a specific ID and its requests.

```
DELETE /problems/:id/requests
```

### Response

```
status: 204 No Content
```
