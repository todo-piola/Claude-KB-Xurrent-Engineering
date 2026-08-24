# Effort Classes - Timesheet Settings API

## List all timesheet settings of an effort class

List all [timesheet\_settings](../../timesheet_settings/index.html) of an effort class with a specific ID.

```
GET /effort_classes/:id/timesheet_settings
```

### Response

```
status: 200 OK
```

```
[{"id":321,"sourceID":null,"name":"8hr workday, 40hr workweek, hours&minutes, 1hr incr.","created_at":"2016-03-22T21:03:35-05:00","updated_at":"2016-03-22T21:03:35-05:00"},{"id":485,"sourceID":null,"name":"7:30 workday, 36hr workweek, hours&minutes, 0:30 incr.","created_at":"2016-03-27T18:53:12-05:00","updated_at":"2016-03-28T22:56:03-05:00"},"..."]
```

The response contains [these fields](../../timesheet_settings/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/effort_classes/:id/timesheet_settings/disabled`: List all disabled timesheet settings of an effort class with a specific ID
- `/effort_classes/:id/timesheet_settings/enabled`: List all enabled timesheet settings of an effort class with a specific ID

## Add a timesheet settings to an effort class

Add a link between an effort class with a specific ID and a timesheet settings with a specific ID.

```
POST /effort_classes/:id/timesheet_settings/:timesheet_setting_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a timesheet settings from an effort class

Remove the link between an effort class with a specific ID and a timesheet settings with a specific ID.

```
DELETE /effort_classes/:id/timesheet_settings/:timesheet_setting_id
```

### Response

```
status: 204 No Content
```

## Remove all timesheet settings from an effort class

Remove all links between an effort class with a specific ID and its timesheet settings.

```
DELETE /effort_classes/:id/timesheet_settings
```

### Response

```
status: 204 No Content
```
