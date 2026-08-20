# Services - Workflow Templates API

## List workflow templates of a service

List all [workflow templates](../../workflow_templates.html) of the service with a specific ID.

```
GET /services/:id/workflow_templates
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:13:47-06:00","sourceID":null,"updated_at":"2016-03-14T03:13:47-06:00","service":{"name":"Windows Server","id":33,"provider":{"name":"Widget Data Center, External IT","id":30}},"subject":"Windows server hardware upgrade","id":9,"disabled":false},{"created_at":"2016-03-14T03:13:47-06:00","sourceID":null,"updated_at":"2016-03-14T03:13:47-06:00","service":{"name":"Personal Computing","id":22,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"subject":"Move desktop personal computer","id":8,"disabled":false,"recurrence":{"start_date":"2016-03-16","day_of_week":true,"day_of_week_index":"first","next_occurrence_at":"2016-04-02T02:00:00-05:00","day_of_week_day":"monday","last_occurrence_at":null,"day":null,"time_of_day":"09:00","day_of_month":null,"interval":1,"ical":"DTSTART;TZID=CET:20160316T000000\nRRULE:FREQ=YEARLY;BYMONTH=1,4,7,10;BYDAY=1MO","disabled":false,"frequency":"yearly","last_occurrence_object":null,"month_of_year":"1,4,7,10","time_zone":"Amsterdam","end_date":null,"last_occurrence_errors":null}},"..."]
```

The response contains [these fields](../../workflow_templates.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/services/:id/workflow_templates/disabled`: List all disabled workflow templates of a service with a specific ID
- `/services/:id/workflow_templates/enabled`: List all enabled workflow templates of a service with a specific ID
