# Projects - Tags API

## List all tags of a project

List all tags of a project with a specific ID.

```
GET /projects/:id/tags
```

### Response

```
status: 200 OK
```

```
[{"id":1,"name":"My Tag"}]
```

## Add a tag to a project

Add a tag to a project by its name.

```
POST /projects/:id/tags
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

## Remove a tag from a project

Remove the link between a project with a specific ID and a tag with a specific ID.

```
DELETE /projects/:id/tags/:tag_id
```

### Response

```
status: 204 No Content
```

## Remove all tags from a project

Remove all links between a project with a specific ID and its tags.

```
DELETE /projects/:id/tags
```

### Response

```
status: 204 No Content
```
