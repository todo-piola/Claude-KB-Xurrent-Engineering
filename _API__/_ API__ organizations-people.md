# Organizations - People API

## List people of an organization

List all [people](../../people.html) of the organization with a specific ID.

```
GET /organizations/:id/people
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

- `/organizations/:id/people/disabled`: List all disabled people of an organization with a specific ID
- `/organizations/:id/people/enabled`: List all enabled people of an organization with a specific ID
