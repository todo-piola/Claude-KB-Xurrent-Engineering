# Service Level Agreements - People API

This API only works for service level agreements whose [Coverage](../../service_level_agreements.html#fields) field value is set to `people`.

## List all people of a service level agreement

List all [people](../../people.html) of a service level agreement with a specific ID.

```
GET /slas/:id/people
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

- `/slas/:id/people/disabled`: List all disabled people of a service level agreement with a specific ID
- `/slas/:id/people/enabled`: List all enabled people of a service level agreement with a specific ID
- `/slas/:id/people/internal`: List all internal people of a service level agreement with a specific ID

## Add a person to a service level agreement

Add a link between a service level agreement with a specific ID and a person with a specific ID.

```
POST /slas/:id/people/:person_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a person from a service level agreement

Remove the link between a service level agreement with a specific ID and a person with a specific ID.

```
DELETE /slas/:id/people/:person_id
```

### Response

```
status: 204 No Content
```

## Remove all people from a service level agreement

Remove all links between a service level agreement with a specific ID and its people.

```
DELETE /slas/:id/people
```

### Response

```
status: 204 No Content
```
