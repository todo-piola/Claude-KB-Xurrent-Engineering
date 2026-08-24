# Calendars - Calendar Hours API

- [List all calendar hours of a calendar](index.html#list-all-calendar-hours-of-a-calendar)
- [Get a single calendar hour of a calendar](index.html#get-a-single-calendar-hour-of-a-calendar)
- [Add calendar hours to a calendar](index.html#add-calendar-hours-to-a-calendar)
- [Update calendar hours of a calendar](index.html#update-calendar-hours-of-a-calendar)
- [Remove calendar hours from a calendar](index.html#remove-calendar-hours-from-a-calendar)
- [Remove all calendar hours from a calendar](index.html#remove-all-calendar-hours-from-a-calendar)
- [Fields](index.html#fields)

## List all calendar hours of a calendar

List all calendar hours of the calendar with a specific ID:

```
GET /calendars/:id/calendar_hours
```

### Response

```
status: 200 OK
```

```
[{"id":4558,"weekday":"mon","time_from":"09:00","time_until":"17:00"}]
```

The response contains [these fields](index.html#fields) by default.

## Get a single calendar hour of a calendar

```
GET /calendars/:id/calendar_hours/:calendar_hour_id
```

### Response

```
status: 200 OK
```

```
{"id":4558,"weekday":"mon","time_from":"09:00","time_until":"17:00"}
```

The response contains [these fields](index.html#fields).

## Add calendar hours to a calendar

Add calendar hours to a calendar with a specific ID.

```
POST /calendars/:id/calendar_hours
```

When creating new calendar hours for a calendar [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":4558,"weekday":"mon","time_from":"09:00","time_until":"17:00"}
```

## Update calendar hours of a calendar

Update calendar hours with a specific ID of a calendar with a specific ID.

```
PATCH /calendars/:id/calendar_hours/:hours_id
```

When updating existing calendar hours for a calendar [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":4558,"weekday":"mon","time_from":"09:00","time_until":"17:00"}
```

## Remove calendar hours from a calendar

Remove calendar hours with a specific ID link from a calendar with a specific ID.

```
DELETE /calendars/:id/calendar_hours/:hours_id
```

### Response

```
status: 204 No Content
```

## Remove all calendar hours from a calendar

Remove all calendar hours from a calendar with a specific ID.

```
DELETE /calendars/:id/calendar_hours/
```

### Response

```
status: 204 No Content
```

## Fields

time\_from
: *Required* **[time of day](../../general/data_types.html)** — The time at which the calendar becomes active on the given weekday.

time\_until
: *Required* **[time of day](../../general/data_types.html)** — The time at which the calendar stops being active on the given weekday.

weekday
: *Required* **[enum](../../general/enumerations/index.html)** — The day of the week. Valid values are:
: - `mon`: Monday
: - `tue`: Tuesday
: - `wed`: Wednesday
: - `thu`: Thursday
: - `fri`: Friday
: - `sat`: Saturday
: - `sun`: Sunday
