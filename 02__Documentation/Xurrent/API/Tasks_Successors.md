# Tasks - Successors API

- [List all successors of a task](index.html#list-all-successors-of-a-task)
- [Add a successor to a task](index.html#add-a-successor-to-a-task)
- [Remove a successor from a task](index.html#remove-a-successor-from-a-task)
- [Remove all successors from a task](index.html#remove-all-successors-from-a-task)

## List all successors of a task

List all successors of a task with a specific ID:

```
GET /tasks/:id/successors
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:14:17-06:00","category":"implementation","finished_at":null,"sourceID":null,"updated_at":"2016-03-14T03:14:17-06:00","member":{"name":"Barney Turban","id":58},"subject":"Inform approvers and requesters of the completion of the workflow","id":95,"impact":"none","team":{"name":"Windows Servers","id":14},"status":"registered","completion_target_at":"2016-03-15T16:33:00-06:00"},"..."]
```

The response contains [these fields](../../tasks.html#collection-fields) by default.

## Add a successor to a task

Add a successor link between a task with a specific ID and another task with a specific ID.

```
POST /tasks/:id/successors/:task_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a successor from a task

Remove the successor link between a task with a specific ID and another task with a specific ID.

```
DELETE /tasks/:id/successors/:task_id
```

### Response

```
status: 204 No Content
```

## Remove all successors from a task

Remove all successor links between a task with a specific ID and its successors.

```
DELETE /tasks/:id/successors
```

### Response

```
status: 204 No Content
```
