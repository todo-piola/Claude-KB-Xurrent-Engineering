# Problems - Tags API

## List all tags of a problem

List all tags of a problem with a specific ID.

```
GET /problems/:id/tags
```

### Response

```
status: 200 OK
```

```
[{"id":1,"name":"My Tag"}]
```

## Add a tag to a problem

Add a tag to a problem by its name.

```
POST /problems/:id/tags
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

## Remove a tag from a problem

Remove the link between a problem with a specific ID and a tag with a specific ID.

```
DELETE /problems/:id/tags/:tag_id
```

### Response

```
status: 204 No Content
```

## Remove all tags from a problem

Remove all links between a problem with a specific ID and its tags.

```
DELETE /problems/:id/tags
```

### Response

```
status: 204 No Content
```
