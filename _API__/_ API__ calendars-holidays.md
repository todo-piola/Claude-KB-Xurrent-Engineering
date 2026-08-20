# Calendars - Holidays API

## List all holidays of a calendar

List all [holidays](../../holidays.html) of a calendar with a specific ID.

```
GET /calendars/:id/holidays
```

### Response

```
status: 200 OK
```

```
[{"picture_uri":null,"name":"2016 Company BBQ","created_at":"2016-03-14T03:09:42-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:42-06:00","end_at":"2016-06-18T00:00:00","start_at":"2016-06-17T16:00:00","id":4,"source":null},{"picture_uri":null,"name":"Christmas 2010","created_at":"2016-03-14T03:09:42-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:42-06:00","end_at":"2010-12-26T00:00:00","start_at":"2010-12-25T00:00:00","id":2,"source":null},"..."]
```

The response contains [these fields](../../holidays.html#collection-fields) by default.

## Add a holiday to a calendar

Add a link between a calendar with a specific ID and a holiday with a specific ID.

```
POST /calendars/:id/holidays/:holiday_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a holiday from a calendar

Remove the link between a calendar with a specific ID and a holiday with a specific ID.

```
DELETE /calendars/:id/holidays/:holiday_id
```

### Response

```
status: 204 No Content
```

## Remove all holidays from a calendar

Remove all links between a calendar with a specific ID and its holidays.

```
DELETE /calendars/:id/holidays
```

### Response

```
status: 204 No Content
```
