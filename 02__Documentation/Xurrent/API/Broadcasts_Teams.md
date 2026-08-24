# Broadcasts - Teams API

## List all teams of a broadcast

List all [teams](../../teams.html) of a broadcast with a specific ID.

```
GET /broadcasts/:id/teams
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

- `/broadcasts/:id/teams/active`: List all active teams of a broadcast with a specific ID
- `/broadcasts/:id/teams/inactive`: List all inactive teams of a broadcast with a specific ID

## Add a team to a broadcast

Add a link between a broadcast with a specific ID and a team with a specific ID.

```
POST /broadcasts/:id/teams/:team_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a team from a broadcast

Remove the link between a broadcast with a specific ID and a team with a specific ID.

```
DELETE /broadcasts/:id/teams/:team_id
```

### Response

```
status: 204 No Content
```

## Remove all teams from a broadcast

Remove all team links from a broadcast with a specific ID.

```
DELETE /broadcasts/:id/teams
```

### Response

```
status: 204 No Content
```
