# Project Task Templates - Project Tasks API

## List project tasks of a project task template

List all [project tasks](../../project_tasks.html) that were created using the project task template with a specific ID.

```
GET /project_task_templates/:id/tasks
```

### Response

```
status: 200 OK
```

```
[{"id":24554,"sourceID":null,"phase":{"completed_at":null,"created_at":"2016-12-23T05:09:06-06:00","id":314,"name":"Implementation","position":3,"started_at":"2016-12-23T05:09:06-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:06-06:00"},"subject":"Go-live","category":"milestone","status":"registered","completion_target_at":"2017-03-01T09:43:00-06:00","finished_at":null,"created_at":"2017-01-18T09:42:39-06:00","updated_at":"2017-01-18T09:42:39-06:00"},{"id":24553,"sourceID":null,"phase":{"completed_at":null,"created_at":"2016-12-23T05:09:06-06:00","id":314,"name":"Implementation","position":3,"started_at":"2016-12-23T05:09:06-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:06-06:00"},"subject":"Training","category":"activity","status":"in_progress","completion_target_at":"2017-03-01T09:43:00-06:00","finished_at":null,"created_at":"2017-01-18T09:42:39-06:00","updated_at":"2017-02-23T10:18:52-06:00"},"..."]
```

The response contains [these fields](../../tasks.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/project_task_templates/:id/tasks/finished`: List all finished project tasks of a project with a specific ID
- `/project_task_templates/:id/tasks/open`: List all open project tasks of a project with a specific ID
