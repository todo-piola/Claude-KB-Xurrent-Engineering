# Workflow Templates - Task Templates API

Consider using the [Task Template Relations API](../task_template_relations.html) instead.

## List all task templates of a workflow template

List all [task templates](../../task_templates.html) of a workflow template with a specific ID.

```
GET /workflow_templates/:id/task_templates
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:13:46-06:00","category":"implementation","sourceID":null,"updated_at":"2016-03-14T03:13:46-06:00","subject":"Inform Operations that events can be ignored","id":40,"impact":"none","disabled":false},{"created_at":"2016-03-14T03:13:46-06:00","category":"approval","sourceID":null,"updated_at":"2016-03-14T03:13:46-06:00","subject":"Windows Server service owner approval","id":39,"impact":null,"disabled":false},"..."]
```

The response contains [these fields](../../task_templates.html#collection-fields).

## Add a task template to a workflow template

Add a link between a workflow template with a specific ID and a task template with a specific ID.

```
POST /workflow_templates/:id/task_templates?task_template_id=:id
POST /workflow_templates/:id/task_templates?task_template_id=:id&phase_name=:name
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a task template from a workflow template

Remove the link between a workflow template with a specific ID and a task template with a specific ID.

```
DELETE /workflow_templates/:id/task_templates/:task_template_id
```

### Response

```
status: 204 No Content
```

## Remove all task templates from a workflow template

Remove all links between a workflow template with a specific ID and its task templates.

```
DELETE /workflow_templates/:id/task_templates
```

### Response

```
status: 204 No Content
```
