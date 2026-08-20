# Risks - Projects API

## List all projects of a risk

List all [projects](../../projects/index.html) who are linked as a project to a risk with a specific ID.

```
GET /risks/:id/projects
```

### Response

```
status: 200 OK
```

```
[{"id":7345,"sourceID":null,"subject":"Warehouse Ordering (WHO)","category":"large","status":"in_progress","completion_target_at":"2017-01-13T09:00:00-06:00","completed_at":null,"service":{"id":41,"name":"Warehouse Management","provider":{"id":44,"name":"Widget Data Center, External IT","account":{"id":"widget","name":"Widget International"}},"localized_name":"Warehouse Management"},"created_at":"2016-11-13T13:17:00-06:00","updated_at":"2016-12-23T05:09:09-06:00"},{"id":4021,"sourceID":null,"subject":"Best in Customer Satisfaction (BICS)","category":"medium","status":"in_progress","completion_target_at":"2017-03-21T10:51:00-05:00","completed_at":null,"service":{"id":24,"name":"Service Management (ITRP)","provider":{"id":44,"name":"Widget Data Center, External IT","account":{"id":"widget","name":"Widget International"}},"localized_name":"Service Management (ITRP)"},"created_at":"2016-08-05T16:12:00-05:00","updated_at":"2017-01-18T16:15:34-06:00"}]
```

The response contains [these fields](../../projects/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/risks/:id/projects/completed`: List all completed projects of a risk with a specific ID
- `/risks/:id/projects/open`: List all open projects of a risk with a specific ID
- `/risks/:id/projects/managed_by_me`: List all projects of a risk with a specific ID which manager is the API user

## Add a project to a risk

Add a link between a risk with a specific ID and a project with a specific ID.

```
POST /risks/:id/projects/:project_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a project from a risk

Remove the link between a risk with a specific ID and a project with a specific ID.

```
DELETE /risks/:id/projects/:project_id
```

### Response

```
status: 204 No Content
```

## Remove all projects from a risk

Remove all links between a risk with a specific ID and its projects.

```
DELETE /risks/:id/projects
```

### Response

```
status: 204 No Content
```
