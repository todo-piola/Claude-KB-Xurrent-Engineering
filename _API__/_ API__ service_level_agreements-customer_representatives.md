# Service Level Agreements - Customer Representatives API

## List all customer representatives of a service level agreement

List all [people](../../people.html) who are a customer representative of a service level agreement with a specific ID.

```
GET /slas/:id/customer_representatives
```

### Response

```
status: 200 OK
```

```
[{"name":"Ashok Kumar","created_at":"2016-03-14T03:09:55-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:31-06:00","manager":{"name":"Howard Tanner","id":5},"id":30,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},{"name":"Barney Turban","created_at":"2016-03-14T03:09:57-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:32-06:00","manager":{"name":"Howard Tanner","id":5},"id":58,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},"..."]
```

The response contains [these fields](../../people.html#collection-fields) by default.

## Add a customer representative to a service level agreement

Add a link between a service level agreement with a specific ID and a customer representative with a specific person ID.

```
POST /slas/:id/customer_representatives/:person_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a customer representative from a service level agreement

Remove the link between a service level agreement with a specific ID and a customer representative with a specific person ID.

```
DELETE /slas/:id/customer_representatives/:person_id
```

### Response

```
status: 204 No Content
```

## Remove all customer representatives from a service level agreement

Remove all links between a service level agreement with a specific ID and its customer representatives.

```
DELETE /slas/:id/customer_representatives
```

### Response

```
status: 204 No Content
```
