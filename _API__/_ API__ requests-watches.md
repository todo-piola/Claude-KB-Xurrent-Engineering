# Requests - Watches API

- [List all watches of a request](../watches.html#list-all-watches-of-a-request)
- [Add a watch to a request](../watches.html#add-a-watch-to-a-request)
- [Update a watch of a request](../watches.html#update-a-watch-of-a-request)
- [Remove a watch from a request](../watches.html#remove-a-watch-from-a-request)
- [Remove all watches from a request](../watches.html#remove-all-watches-from-a-request)
- [Fields](../watches.html#fields)

## List all watches of a request

List all watches of the [request](../../requests.html) with a specific ID:

```
GET /requests/:id/watches
```

### Response

```
status: 200 OK
```

```
[{"added_by":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"created_at":"2023-02-01T05:14:45-06:00","id":4580,"person":{"id":567,"name":"Tom Waters","account":{"id":"widget","name":"Widget International"}},"updated_at":"2023-02-01T05:14:45-06:00","account":{"id":"widget","name":"Widget International"}},{"added_by":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"created_at":"2023-02-01T05:14:45-06:00","id":4581,"person":{"id":208,"name":"Ellen Brown","account":{"id":"widget","name":"Widget International"}},"updated_at":"2023-02-01T05:14:45-06:00","account":{"id":"widget","name":"Widget International"}}]
```

The response contains [these fields](../watches.html#fields) by default.

## Add a watch to a request

Add a watch to a request with a specific ID.

```
POST /requests/:id/watches
```

When creating a new watch for a request [these fields](../watches.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"added_by":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"created_at":"2023-02-01T05:14:45-06:00","id":4580,"person":{"id":567,"name":"Tom Waters","account":{"id":"widget","name":"Widget International"}},"updated_at":"2023-02-01T05:14:45-06:00","account":{"id":"widget","name":"Widget International"}}
```

## Update a watch of a request

Update a watch of a request with a specific ID.

```
PATCH /requests/:id/watches/:watch_id
```

When updating an existing watch for a request [these fields](../watches.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"status":"registered","...":"..."}
```

## Remove a watch from a request

Remove a watch with a specific ID from a request with a specific ID.

```
DELETE /requests/:id/watches/:watch_id
```

### Response

```
status: 204 No Content
```

## Remove all watches from a request

Remove all watch from a request with a specific ID.

```
DELETE /requests/:id/watches/
```

### Response

```
status: 204 No Content
```

## Fields

added\_by
: *Readonly* **[reference](../../general/data_types.html#references) to [Person](../../people.html)** — The person who created the watch.

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the watch was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the watch.

person
: *Required* **[reference](../../general/data_types.html#references) to [Person](../../people.html)** — The person who is selected as the watcher.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the watch. If the watch has had no updates it contains the `created_at` value.
