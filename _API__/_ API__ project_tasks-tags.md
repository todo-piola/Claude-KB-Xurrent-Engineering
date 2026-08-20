# Project Tasks - Tags API

## List all tags of a project task

List all tags of a project task with a specific ID.

```
GET /project_tasks/:id/tags
```

### Response

```
status: 200 OK
```

```
[{"id":1,"name":"My Tag"}]
```

## Add a tag to a project task

Add a tag to a project task by its name.

```
POST /project_tasks/:id/tags
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

## Remove a tag from a project task

Remove the link between a project task with a specific ID and a tag with a specific ID.

```
DELETE /project_tasks/:id/tags/:tag_id
```

### Response

```
status: 204 No Content
```

## Remove all tags from a project task

Remove all links between a project task with a specific ID and its tags.

```
DELETE /project_tasks/:id/tags
```

### Response

```
status: 204 No Content
```
