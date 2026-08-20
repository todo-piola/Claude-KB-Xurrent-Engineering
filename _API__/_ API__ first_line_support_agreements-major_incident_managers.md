# First Line Support Agreements - Major Incident Managers API

## List all major incident managers of a first line support agreement

List all [people](../../people.html) who are a major incident manager of a first line support agreement with a specific ID.

```
GET /flsas/:id/major_incident_managers
```

### Response

```
status: 200 OK
```

```
[{"name":"Ashok Kumar","created_at":"2016-03-14T03:09:55-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:31-06:00","manager":{"name":"Howard Tanner","id":5},"id":30,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},{"name":"Barney Turban","created_at":"2016-03-14T03:09:57-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:32-06:00","manager":{"name":"Howard Tanner","id":5},"id":58,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},"..."]
```

The response contains [these fields](../../people.html#collection-fields) by default.

## Add a major incident manager to a first line support agreement

Add a link between a first line support agreement with a specific ID and a major incident manager with a specific person ID.

```
POST /flsas/:id/major_incident_managers/:person_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a major incident manager from a first line support agreement

Remove the link between a first line support agreement with a specific ID and a major incident manager with a specific person ID.

```
DELETE /flsas/:id/major_incident_managers/:person_id
```

### Response

```
status: 204 No Content
```

## Remove all major incident managers from a first line support agreement

Remove all links between a first line support agreement with a specific ID and its major incident managers.

```
DELETE /flsas/:id/major_incident_managers
```

### Response

```
status: 204 No Content
```
