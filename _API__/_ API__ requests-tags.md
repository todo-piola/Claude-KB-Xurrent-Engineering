# Requests - Tags API

## List all tags of a request

List all tags of a request with a specific ID.

```
GET /requests/:id/tags
```

### Response

```
status: 200 OK
```

```
[{"id":1,"name":"My Tag"}]
```

## Add a tag to a request

Add a tag to a request by its name.

```
POST /requests/:id/tags
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

## Remove a tag from a request

Remove the link between a request with a specific ID and a tag with a specific ID.

```
DELETE /requests/:id/tags/:tag_id
```

### Response

```
status: 204 No Content
```

## Remove all tags from a request

Remove all links between a request with a specific ID and its tags.

```
DELETE /requests/:id/tags
```

### Response

```
status: 204 No Content
```
