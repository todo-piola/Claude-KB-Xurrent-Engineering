# Task Templates - Approvals API

- [List all approvals of a task](../approvals.html#list-all-approvals-of-a-project-task)
- [Add an approval to a task](../approvals.html#add-an-approval-to-a-project-task)
- [Update an approval of a task](../approvals.html#update-an-approval-of-a-project-task)
- [Remove an approval from a task](../approvals.html#remove-an-approval-from-a-project-task)
- [Remove all approvals from a task](../approvals.html#remove-all-approvals-from-a-project-task)
- [Fields](../approvals.html#fields)

## List all approvals of a task template

List all approvals of the [task template](../../task_templates.html) with a specific ID:

```
GET /task_templates/:id/approvals
```

### Response

```
status: 200 OK
```

```
[{"approver":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"id":2,"planned_effort":240},{"approver":{"id":82,"name":"Beatrice Baldwin","account":{"id":"widget","name":"Widget International"}},"id":24,"planned_effort":180},"..."]
```

The response contains [these fields](../approvals.html#fields) by default.

## Add an approval to a task template

Add an approval to a task template with a specific ID.

```
POST /task_templates/:id/approvals
```

When creating a new approval for a task template [these fields](../approvals.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"approver":{"id":50378,"name":"Matt Leach"},"id":16093,"planned_effort":180}
```

## Update an approval of a task template

Update an approval of a task template with a specific ID.

```
PATCH /task_templates/:id/approvals/:approval_id
```

When updating an existing approval for a task template [these fields](../approvals.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"planned_effort":180,"...":"..."}
```

## Remove an approval from a task template

Remove an approval with a specific ID from a task template with a specific ID.

```
DELETE /task_templates/:id/approvals/:approval_id
```

### Response

```
status: 204 No Content
```

## Remove all approvals from a task template

Remove all approval from a task template with a specific ID.

```
DELETE /task_templates/:id/approvals/
```

### Response

```
status: 204 No Content
```

## Fields

approver
: *Required* **[reference](../../general/data_types.html#references) to [Person](../../people.html)** — The ID of the person who is selected as the approver for the task template approval.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the task template approval.

planned\_effort
: *Optional* **[integer](../../general/data_types.html) (max 600000)** — The Planned effort field is used to enter the number of minutes the approver is expected to spend working on a task that was created based on the task template to which the approval belongs.
