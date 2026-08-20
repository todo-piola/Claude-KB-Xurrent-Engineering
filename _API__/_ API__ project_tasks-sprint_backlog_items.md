# Project Tasks - Sprint Backlog Items API

## List sprint backlog items of a project task

List all [sprint backlog items](../../sprints/backlog_items/index.html) of the project task with a specific ID.

```
GET /project_tasks/:id/sprint_backlog_items
```

### Response

```
status: 200 OK
```

```
[{"id":26,"position":1,"estimate":13,"created_at":"2022-10-06T04:48:56-05:00","updated_at":"2022-10-06T04:48:56-05:00","sprint":{"id":566,"scrum_workspace":{"id":1,"name":"Application Development","nodeID":"..."},"number":2,"nodeID":"..."},"nodeID":"...","request":{"id":70260,"subject":"Add ability to specify variance limits to the Quality Control application","account":{"id":"wna-it","name":"Widget N. America - IT"},"nodeID":"..."}},"..."]
```

The response contains [these fields](../../sprints/backlog_items/index.html#collection-fields) by default.
