# Project Tasks - Predecessors API

- [List all predecessors of a project task](index.html#list-all-predecessors-of-a-project-task)
- [Add a predecessor to a project task](index.html#add-a-predecessor-to-a-project-task)
- [Remove a predecessor from a project task](index.html#remove-a-predecessor-from-a-project-task)
- [Remove all predecessors from a project task](index.html#remove-all-predecessors-from-a-project-task)

## List all predecessors of a project task

List all predecessors of a project task with a specific ID:

```
GET /project_tasks/:id/predecessors
```

### Response

```
status: 200 OK
```

```
[{"id":24554,"sourceID":null,"phase":{"completed_at":null,"created_at":"2016-12-23T05:09:06-06:00","id":314,"name":"Implementation","position":3,"started_at":"2016-12-23T05:09:06-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:06-06:00"},"subject":"Go-live","category":"milestone","status":"registered","completion_target_at":"2017-03-01T09:43:00-06:00","finished_at":null,"created_at":"2017-01-18T09:42:39-06:00","updated_at":"2017-01-18T09:42:39-06:00"},{"id":24553,"sourceID":null,"phase":{"completed_at":null,"created_at":"2016-12-23T05:09:06-06:00","id":314,"name":"Implementation","position":3,"started_at":"2016-12-23T05:09:06-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:06-06:00"},"subject":"Training","category":"activity","status":"in_progress","completion_target_at":"2017-03-01T09:43:00-06:00","finished_at":null,"created_at":"2017-01-18T09:42:39-06:00","updated_at":"2017-02-23T10:18:52-06:00"},"..."]
```

The response contains [these fields](../../project_tasks.html#collection-fields) by default.

## Add a predecessor to a project task

Add a predecessor link between a project task with a specific ID and another project task with a specific ID.

```
POST /project_tasks/:id/predecessors/:project_task_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a predecessor from a project task

Remove the predecessor link between a project task with a specific ID and another project task with a specific ID.

```
DELETE /project_tasks/:id/predecessors/:project_task_id
```

### Response

```
status: 204 No Content
```

## Remove all predecessors from a project task

Remove all predecessor links between a project task with a specific ID and its predecessors.

```
DELETE /project_tasks/:id/predecessors
```

### Response

```
status: 204 No Content
```
