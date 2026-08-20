# Workflows - Tasks API

## List all tasks of a workflow

List all [tasks](../../tasks.html) of a workflow with a specific ID.

```
GET /workflows/:id/tasks
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:14:17-06:00","category":"implementation","finished_at":null,"sourceID":null,"updated_at":"2016-03-14T03:14:17-06:00","member":{"name":"Barney Turban","id":58},"subject":"Inform approvers and requesters of the completion of the workflow","id":95,"impact":"none","team":{"name":"Windows Servers","id":14},"status":"registered","completion_target_at":"2016-03-15T16:33:00-06:00"},"..."]
```

The response contains [these fields](../../tasks.html#collection-fields) by default.

**Important**: As long as the workflow has the status `being_created` a **Not Found** response will be returned:

```
status: 404 Not Found
```

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/workflows/:id/tasks/finished`: List all finished tasks of a workflow with a specific ID
- `/workflows/:id/tasks/open`: List all open tasks of a workflow with a specific ID

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](../../tasks.html#fields):

`category` `member` `status` `template`
