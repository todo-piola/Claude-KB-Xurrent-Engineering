# Broadcasts - Customers API

## List all customers of a broadcast

List all [customers](../../organizations.html) of a broadcast with a specific ID.

```
GET /broadcasts/:id/customers
```

### Response

```
status: 200 OK
```

```
[{"id":44,"sourceID":null,"name":"Widget Data Center, External IT","parent":{"id":6,"name":"Widget Data Center"},"manager":{"id":6,"name":"Howard Tanner"},"created_at":"2016-03-22T21:02:50-05:00","updated_at":"2016-03-25T16:54:52-05:00"},{"id":50,"sourceID":null,"name":"Widget North America, Finance","parent":{"id":51,"name":"Widget North America, Inc."},"manager":{"id":120,"name":"Carolyn Goldrat"},"created_at":"2016-03-22T21:02:50-05:00","updated_at":"2016-03-22T21:03:36-05:00"},"..."]
```

The response contains [these fields](../../organizations.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/broadcasts/:id/customers/disabled`: List all disabled customers of a broadcast with a specific ID
- `/broadcasts/:id/customers/enabled`: List all enabled customers of a broadcast with a specific ID
- `/broadcasts/:id/customers/external`: List all external customers of a broadcast with a specific ID
- `/broadcasts/:id/customers/internal`: List all internal customers of a broadcast with a specific ID
- `/broadcasts/:id/customers/directory`: List all customers of a broadcast with a specific ID registered in the directory account of the support domain account from which the data is requested
- `/broadcasts/:id/customers/support_domain`: List all customers of a broadcast with a specific ID registered in the account from which the data is requested
- `/broadcasts/:id/customers/managed_by_me`: List all customers of a broadcast with a specific ID which manager or substitute is the API user

## Add a customer to a broadcast

Add a link between a broadcast with a specific ID and a customer with a specific ID.

```
POST /broadcasts/:id/customers/:organization_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a customer from a broadcast

Remove the link between a broadcast with a specific ID and a customer with a specific ID.

```
DELETE /broadcasts/:id/customers/:organization_id
```

### Response

```
status: 204 No Content
```
