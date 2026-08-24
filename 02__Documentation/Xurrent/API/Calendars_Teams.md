# Calendars - Teams API

## List teams of a calendar

List all [teams](../../teams.html) of a calendar with a specific ID.

```
GET /calendars/:id/teams
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

- `/calendars/:id/teams/disabled`: List all disabled teams of a calendar with a specific ID
- `/calendars/:id/teams/enabled`: List all enabled teams of a calendar with a specific ID
