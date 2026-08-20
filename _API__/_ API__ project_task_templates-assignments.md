# Project Task Templates - Assignments API

- [List all assignments of a project task](../assignments.html#list-all-assignments-of-a-project-task)
- [Add an assignment to a project task](../assignments.html#add-an-assignment-to-a-project-task)
- [Update an assignment of a project task](../assignments.html#update-an-assignment-of-a-project-task)
- [Remove an assignment from a project task](../assignments.html#remove-an-assignment-from-a-project-task)
- [Remove all assignments from a project task](../assignments.html#remove-all-assignments-from-a-project-task)
- [Fields](../assignments.html#fields)

## List all assignments of a project task template

List all assignments of the [project task template](../../project_task_templates.html) with a specific ID:

```
GET /project_task_templates/:id/assignments
```

### Response

```
status: 200 OK
```

```
[{"assignee":{"id":48317,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"id":14752,"planned_effort":60},{"assignee":{"id":49091,"name":"Nathan Stadler","account":{"id":"widget","name":"Widget International"}},"id":14753,"planned_effort":60}]
```

The response contains [these fields](../assignments.html#fields) by default.

## Add an assignment to a project task template

Add an assignment to a project task template with a specific ID.

```
POST /project_task_templates/:id/assignments
```

When creating a new assignment for a project task template [these fields](../assignments.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"assignee":{"id":50378,"name":"Matt Leach"},"id":16093,"planned_effort":180}
```

## Update an assignment of a project task template

Update an assignment of a project task template with a specific ID.

```
PATCH /project_task_templates/:id/assignments/:assignment_id
```

When updating an existing assignment for a project task template [these fields](../assignments.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"planned_effort":180,"...":"..."}
```

## Remove an assignment from a project task template

Remove an assignment with a specific ID from a project task template with a specific ID.

```
DELETE /project_task_templates/:id/assignments/:assignment_id
```

### Response

```
status: 204 No Content
```

## Remove all assignments from a project task template

Remove all assignment from a project task template with a specific ID.

```
DELETE /project_task_templates/:id/assignments/
```

### Response

```
status: 204 No Content
```

## Fields

assignee
: *Required* **[reference](../../general/data_types.html#references) to [Person](../../people.html)** — The ID of the person who is selected as the assignee for the project task template assignment.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the project task template assignment.

planned\_effort
: *Optional* **[integer](../../general/data_types.html) (max 600000)** — The Planned effort field is used to enter the number of minutes the assignee is expected to spend working on a project task that was created based on the project task template to which the assignment belongs.
