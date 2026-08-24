# People - Out of Office Periods API

## List all out of office periods of a person

List all [out of office periods](../../out_of_office_periods.html) of a person with a specific ID.

```
GET /people/:id/out_of_office_periods
```

### Response

```
status: 200 OK
```

```
[{"id":3,"sourceID":null,"person":{"id":196,"name":"Ellen Brown"},"start_at":"2019-11-18T06:00:00Z","end_at":"2019-11-18T15:45:15Z","created_at":"2019-11-18T08:10:52-06:00","updated_at":"2019-11-18T09:45:16-06:00"},"..."]
```

The response contains [these fields](../../out_of_office_periods.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/people/:id/out_of_office_periods/open`: List all out of office periods for which the end time is in the future
- `/people/:id/out_of_office_periods/completed`: List all out of office periods for which the end time is in the past

## Get a single out of office period of a person

```
GET /people/:id/out_of_office_periods/:id
```

### Response

```
status: 200 OK
```

```
{"approval_delegate":null,"created_at":"2019-11-18T08:10:52-06:00","end_at":"2019-11-18T15:45:15Z","id":3,"person":{"id":196,"name":"Ellen Brown"},"reason":"Time Off - Vacation","source":"4me","sourceID":null,"start_at":"2019-11-18T06:00:00Z","time_allocation":{"id":2,"group":"Time Off","name":"Vacation","account":{"id":"wdc","name":"Widget Data Center"},"localized_name":"Vacation"},"updated_at":"2019-11-18T09:45:16-06:00"}
```

The response contains [these fields](../../out_of_office_periods.html#fields).
