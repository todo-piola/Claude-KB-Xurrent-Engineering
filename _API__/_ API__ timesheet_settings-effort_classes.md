# Timesheet Settings - Effort Classes API

## List all effort classes of a timesheet settings

List all [effort classes](../../effort_classes.html) of a timesheet settings with a specific ID.

```
GET /timesheet_settings/:id/effort_classes
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"name":"Standard","position":1,"cost_multiplier":"1.0","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"name":"Overtime","position":2,"cost_multiplier":"1.65","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"}]
```

The response contains [these fields](../../effort_classes.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/timesheet_settings/:id/effort_classes/disabled`: List all disabled effort classes of a timesheet settings with a specific ID
- `/timesheet_settings/:id/effort_classes/enabled`: List all enabled effort classes of a timesheet settings with a specific ID

## Add an effort class to a timesheet settings

Add a link between a timesheet settings with a specific ID and an effort class with a specific ID.

```
POST /timesheet_settings/:id/effort_classes/:effort_class_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove an effort class from a timesheet settings

Remove the link between a timesheet settings with a specific ID and an effort class with a specific ID.

```
DELETE /timesheet_settings/:id/effort_classes/:effort_class_id
```

### Response

```
status: 204 No Content
```

## Remove all effort classes from a timesheet settings

Remove all links between a timesheet settings with a specific ID and its effort classes.

```
DELETE /timesheet_settings/:id/effort_classes
```

### Response

```
status: 204 No Content
```
