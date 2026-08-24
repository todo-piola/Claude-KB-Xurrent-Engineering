# Workflow Templates - Task Template Relations API

Use this API to view or update the relations between a workflow template and its task templates.

- [List all task template relations of a workflow template](../task_template_relations.html#list-all-task-template-relations-of-a-workflow-template)
- [Add a task template relation to a workflow template](../task_template_relations.html#add-a-task-template-relation-to-a-workflow-template)
- [Update a task template relation of a workflow template](../task_template_relations.html#update-a-task-template-relation-of-a-workflow-template)
- [Remove a task template relation from a workflow template](../task_template_relations.html#remove-a-task-template-relation-from-a-workflow-template)
- [Remove all task template relations from a workflow template](../task_template_relations.html#remove-all-task-template-relations-from-a-workflow-template)
- [Fields](../task_template_relations.html#fields)

## List all task template relations of a workflow template

List all of the task template relations of a workflow template with a specific ID:

```
GET /workflow_templates/:id/task_template_relations
```

### Response

```
status: 200 OK
```

```
[{"id":4558,"...":"..."}]
```

The response contains [these fields](../task_template_relations.html#fields) by default.

## Add a task template relation to a workflow template

Add a task template relation to a workflow template with a specific ID.

```
POST /workflow_templates/:id/task_template_relations
```

When creating a new task template relation for a workflow template [these fields](../task_template_relations.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":4558,"...":"..."}
```

## Update a task template relation of a workflow template

Update a task template relation with a specific ID of a workflow template with a specific ID.

```
PATCH /workflow_templates/:id/task_template_relations/:task_template_relation_id
```

When updating an existing task template relation for a workflow template [these fields](../task_template_relations.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":4558,"...":"..."}
```

## Remove a task template relation from a workflow template

Remove a task template relation with a specific ID from a workflow template with a specific ID.

```
DELETE /workflow_templates/:id/task_template_relations/:task_template_relation_id
```

### Response

```
status: 204 No Content
```

## Remove all task template relations from a workflow template

Remove all task template relations from a workflow template with a specific ID.

```
DELETE /workflow_templates/:id/task_template_relations
```

### Response

```
status: 204 No Content
```

## Fields

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the task template relation was created.

id
: *Required* **[integer](../../general/data_types.html)** — The unique ID of the relation between the workflow template and the task template.

phase\_name
: *Optional* **[string](../../general/data_types.html) (max 50)** — The Phase Name field indicates the phase of the workflow template that the task template relation is a part of.

task\_template
: *Required* **[reference](../../general/data_types.html#references) to [task template](../../task_templates.html)** — The related task template.

failure\_task\_template
: *Optional* **[reference](../../general/data_types.html#references) to [task template](../../task_templates.html)** — The template of the task that will be assigned in case this task is failed or rejected.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the task template relation. If the task template relation has no updates it contains the `created_at` value.
