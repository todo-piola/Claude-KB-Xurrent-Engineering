# Tasks - Tags API

## List all tags of a task

List all tags of a task with a specific ID.

```
GET /tasks/:id/tags
```

### Response

```
status: 200 OK
```

```
[{"id":1,"name":"My Tag"}]
```

## Add a tag to a task

Add a tag to a task by its name.

```
POST /tasks/:id/tags
```

Body:

```
{"name":"My Tag"}
```

### Response

```
status: 200 OK
```

```
{"id":1,"name":"My Tag"}
```

## Remove a tag from a task

Remove the link between a task with a specific ID and a tag with a specific ID.

```
DELETE /tasks/:id/tags/:tag_id
```

### Response

```
status: 204 No Content
```

## Remove all tags from a task

Remove all links between a task with a specific ID and its tags.

```
DELETE /tasks/:id/tags
```

### Response

```
status: 204 No Content
```
