# Project Tasks - Assignments API

- [List all assignments of a project task](../assignments.html#list-all-assignments-of-a-project-task)
- [Add an assignment to a project task](../assignments.html#add-an-assignment-to-a-project-task)
- [Update an assignment of a project task](../assignments.html#update-an-assignment-of-a-project-task)
- [Remove an assignment from a project task](../assignments.html#remove-an-assignment-from-a-project-task)
- [Remove all assignments from a project task](../assignments.html#remove-all-assignments-from-a-project-task)
- [Fields](../assignments.html#fields)

## List all assignments of a project task

List all assignments of the [project task](../../project_tasks.html) with a specific ID:

```
GET /project_tasks/:id/assignments
```

### Response

```
status: 200 OK
```

```
[{"assignee":{"id":156,"name":"Ellen Brown","account":{"id":"widget","name":"Widget International"}},"attachment":null,"created_at":"2016-12-23T05:09:09-06:00","id":75,"planned_effort":240,"status":"waiting_for","updated_at":"2017-01-19T13:34:25-06:00","waiting_until":"2017-01-22T15:00:00Z","account":{"id":"widget","name":"Widget International"}},{"assignee":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"attachment":null,"created_at":"2017-01-19T13:24:16-06:00","id":107,"planned_effort":null,"status":"assigned","updated_at":"2017-01-19T13:33:59-06:00","waiting_until":null,"account":{"id":"widget","name":"Widget International"}}]
```

The response contains [these fields](../assignments.html#fields) by default.

## Add an assignment to a project task

Add an assignment to a project task with a specific ID.

```
POST /project_tasks/:id/assignments
```

When creating a new assignment for a project task [these fields](../assignments.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"assignee":{"id":41,"name":"Beatrice Baldwin"},"account":{"id":"widget","name":"Widget International"},"attachment":null,"created_at":"2017-01-19T13:55:32-06:00","id":109,"status":"assigned","updated_at":"2017-01-19T13:55:32-06:00"}
```

## Update an assignment of a project task

Update an assignment of a project task with a specific ID.

```
PATCH /project_tasks/:id/assignments/:assignment_id
```

When updating an existing assignment for a project task [these fields](../assignments.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"status":"registered","...":"..."}
```

## Remove an assignment from a project task

Remove an assignment with a specific ID from a project task with a specific ID.

```
DELETE /project_tasks/:id/assignments/:assignment_id
```

### Response

```
status: 204 No Content
```

## Remove all assignments from a project task

Remove all assignment from a project task with a specific ID.

```
DELETE /project_tasks/:id/assignments/
```

### Response

```
status: 204 No Content
```

## Fields

assignee
: *Required* **[reference](../../general/data_types.html#references) to [Person](../../people.html)** — The ID of the person who is selected as the assignee for the assignment.

attachment
: *Readonly* **link to Project Summary** — The hyperlink to the Project Summary PDF file that was generated for the assignee when the assignment was last set to the status `assigned` (for project tasks of the category `approval` only).

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the assignment was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the assignment.

planned\_effort
: *Optional* **[integer](../../general/data_types.html) (max 600000)** — The Planned effort field is used to enter the number of minutes the assignee is expected to spend working on the project task to which the assignment belongs.

status
: *Readonly* **[enum](../../general/enumerations/index.html)** — The status of the assignment. Valid values are:
: - `registered`
 - `assigned`
 - `accepted`
 - `in_progress`
 - `waiting_for`
 - `failed`
 - `rejected`
 - `completed`
 - `approved`
 - `canceled`

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the assignment. If the assignment has had no updates it contains the `created_at` value.

waiting\_until
: *Optional* **[datetime](../../general/data_types.html)** — The Waiting until field is used to specify the date and time at which the status of the assignment is to be updated from `waiting_for` to `assigned`. This field is available only when the Status field is set to `waiting_for`.
