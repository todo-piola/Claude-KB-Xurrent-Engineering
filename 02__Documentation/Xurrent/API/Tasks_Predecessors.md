# Tasks - Predecessors API

- [List all predecessors of a task](index.html#list-all-predecessors-of-a-task)
- [Add a predecessor to a task](index.html#add-a-predecessor-to-a-task)
- [Remove a predecessor from a task](index.html#remove-a-predecessor-from-a-task)
- [Remove all predecessors from a task](index.html#remove-all-predecessors-from-a-task)

## List all predecessors of a task

List all predecessors of a task with a specific ID:

```
GET /tasks/:id/predecessors
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:14:17-06:00","category":"implementation","finished_at":null,"sourceID":null,"updated_at":"2016-03-14T03:14:17-06:00","member":{"name":"Barney Turban","id":58},"subject":"Inform approvers and requesters of the completion of the workflow","id":95,"impact":"none","team":{"name":"Windows Servers","id":14},"status":"registered","completion_target_at":"2016-03-15T16:33:00-06:00"},"..."]
```

The response contains [these fields](../../tasks.html#collection-fields) by default.

## Add a predecessor to a task

Add a predecessor link between a task with a specific ID and another task with a specific ID.

```
POST /tasks/:id/predecessors/:task_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a predecessor from a task

Remove the predecessor link between a task with a specific ID and another task with a specific ID.

```
DELETE /tasks/:id/predecessors/:task_id
```

### Response

```
status: 204 No Content
```

## Remove all predecessors from a task

Remove all predecessor links between a task with a specific ID and its predecessors.

```
DELETE /tasks/:id/predecessors
```

### Response

```
status: 204 No Content
```
