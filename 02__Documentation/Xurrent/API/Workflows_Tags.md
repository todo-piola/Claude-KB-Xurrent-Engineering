# Workflows - Tags API

## List all tags of a workflow

List all tags of a workflow with a specific ID.

```
GET /workflows/:id/tags
```

### Response

```
status: 200 OK
```

```
[{"id":1,"name":"My Tag"}]
```

## Add a tag to a workflow

Add a tag to a workflow by its name.

```
POST /workflows/:id/tags
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

## Remove a tag from a workflow

Remove the link between a workflow with a specific ID and a tag with a specific ID.

```
DELETE /workflows/:id/tags/:tag_id
```

### Response

```
status: 204 No Content
```

## Remove all tags from a workflow

Remove all links between a workflow with a specific ID and its tags.

```
DELETE /workflows/:id/tags
```

### Response

```
status: 204 No Content
```
