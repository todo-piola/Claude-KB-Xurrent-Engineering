# Configuration Items - Users API

## List all users of a configuration item

List all [People](../../people.html) who are linked as a user to a configuration item with a specific ID.

```
GET /cis/:id/users
```

### Response

```
status: 200 OK
```

```
[{"name":"Ashok Kumar","created_at":"2016-03-14T03:09:55-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:31-06:00","manager":{"name":"Howard Tanner","id":5},"id":30,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},{"name":"Barney Turban","created_at":"2016-03-14T03:09:57-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:32-06:00","manager":{"name":"Howard Tanner","id":5},"id":58,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},"..."]
```

The response contains [these fields](../../people.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/cis/:id/users/disabled`: List all disabled users of a configuration item with a specific ID
- `/cis/:id/users/enabled`: List all enabled users of a configuration item with a specific ID
- `/cis/:id/users/internal`: List all internal users of a configuration item with a specific ID

## Add a user to a configuration item

Add a link between a configuration item with a specific ID and a Person with a specific ID.

```
POST /cis/:id/users/:person_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a user from a configuration item

Remove the link between a configuration item with a specific ID and a Person with a specific ID.

```
DELETE /cis/:id/users/:person_id
```

### Response

```
status: 204 No Content
```

## Remove all users from a configuration item

Remove all links between a configuration item with a specific ID and its users.

```
DELETE /cis/:id/users
```

### Response

```
status: 204 No Content
```
