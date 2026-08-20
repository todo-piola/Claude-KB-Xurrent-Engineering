# Teams - Members API

## List all members of a team

List all [people](../../people.html) who are linked as a member to a team with a specific ID.

```
GET /teams/:id/members
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

- `/teams/:id/members/disabled`: List all disabled people of a team with a specific ID
- `/teams/:id/members/enabled`: List all enabled people of a team with a specific ID
- `/teams/:id/members/internal`: List all enabled people of a team with a specific ID

## Add a member to a team

Add a link between a team with a specific ID and a person with a specific ID to make this person a member of the team.

```
POST /teams/:id/members/:person_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a member from a team

Remove the membership link between a team with a specific ID and a person with a specific ID.

```
DELETE /teams/:id/members/:person_id
```

### Response

```
status: 204 No Content
```

## Remove all members from a team

Remove all links between a team with a specific ID and its members.

```
DELETE /teams/:id/members
```

### Response

```
status: 204 No Content
```
