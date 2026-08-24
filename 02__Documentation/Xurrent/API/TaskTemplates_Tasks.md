# Task Templates - Tasks API

## List tasks of a task template

List all [tasks](../../tasks.html) that were created using the task template with a specific ID.

```
GET /task_templates/:id/tasks
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:14:17-06:00","category":"implementation","finished_at":null,"sourceID":null,"updated_at":"2016-03-14T03:14:17-06:00","member":{"name":"Barney Turban","id":58},"subject":"Inform approvers and requesters of the completion of the workflow","id":95,"impact":"none","team":{"name":"Windows Servers","id":14},"status":"registered","completion_target_at":"2016-03-15T16:33:00-06:00"},"..."]
```

The response contains [these fields](../../tasks.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/task_templates/:id/tasks/finished`: List all finished tasks of a task template with a specific ID
- `/task_templates/:id/tasks/open`: List all open tasks of a task template with a specific ID

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](index.html#/v1/tasks/#fields):

`status`
