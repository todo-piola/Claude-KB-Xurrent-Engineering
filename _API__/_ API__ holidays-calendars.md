# Holidays - Calendars API

## List all calendars of a holiday

List all [calendars](../../calendars/index.html) of a holiday with a specific ID.

```
GET /holidays/:id/calendars
```

### Response

```
status: 200 OK
```

```
[{"name":"24x5 (Monday through Friday)","created_at":"2016-03-14T03:09:47-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:47-06:00","id":32,"calendar_hours":[{"time_until":"00:00","time_from":"00:00","weekday":"mon"},{"time_until":"00:00","time_from":"00:00","weekday":"tue"},{"time_until":"00:00","time_from":"00:00","weekday":"wed"},{"time_until":"00:00","time_from":"00:00","weekday":"thu"},{"time_until":"00:00","time_from":"00:00","weekday":"fri"}],"source":null,"disabled":true},{"name":"24x6 (Monday through Saturday)","created_at":"2016-03-14T03:09:47-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:47-06:00","id":33,"calendar_hours":[{"time_until":"00:00","time_from":"00:00","weekday":"mon"},{"time_until":"00:00","time_from":"00:00","weekday":"tue"},{"time_until":"00:00","time_from":"00:00","weekday":"wed"},{"time_until":"00:00","time_from":"00:00","weekday":"thu"},{"time_until":"00:00","time_from":"00:00","weekday":"fri"},{"time_until":"00:00","time_from":"00:00","weekday":"sat"}],"source":null},"..."]
```

The response contains [these fields](../../calendars/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/holidays/:id/calendars/disabled`: List all disabled calendars of a holiday with a specific ID
- `/holidays/:id/calendars/enabled`: List all enabled calendars of a holiday with a specific ID

## Add a calendar to a holiday

Add a link between a holiday with a specific ID and a calendar with a specific ID.

```
POST /holidays/:id/calendars/:calendar_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a calendar from a holiday

Remove the link between a holiday with a specific ID and a calendar with a specific ID.

```
DELETE /holidays/:id/calendars/:calendar_id
```

### Response

```
status: 204 No Content
```

## Remove all calendars from a holiday

Remove all links between a holiday with a specific ID and its calendars.

```
DELETE /holidays/:id/calendars
```

### Response

```
status: 204 No Content
```
