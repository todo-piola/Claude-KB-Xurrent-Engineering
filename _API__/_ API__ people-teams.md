# People - Teams API

## List all teams of a person

List all [teams](../../teams.html) of a person with a specific ID.

```
GET /people/:id/teams
```

### Response

```
status: 200 OK
```

```
[{"name":"Application Development","created_at":"2016-03-14T03:10:36-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:36-06:00","id":7,"disabled":false},{"name":"Database Administration","created_at":"2016-03-14T03:10:36-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:36-06:00","id":8,"disabled":false},"..."]
```

The response contains [these fields](../../teams.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/people/:id/teams/disabled`: List all disabled teams of a person with a specific ID
- `/people/:id/teams/enabled`: List all enabled teams of a person with a specific ID

## Add a team to a person

Add a link between a person with a specific ID and a team with a specific ID.

```
POST /people/:id/teams/:team_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a team from a person

Remove the link between a person with a specific ID and a team with a specific ID.

```
DELETE /people/:id/teams/:team_id
```

### Response

```
status: 204 No Content
```

## Remove all teams from a person

Remove all links between a person with a specific ID and its teams.

```
DELETE /people/:id/teams
```

### Response

```
status: 204 No Content
```
