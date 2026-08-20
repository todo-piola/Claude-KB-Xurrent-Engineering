# Tasks - Approvals API

- [List all approvals of a task](../approvals.html#list-all-approvals-of-a-task)
- [Add an approval to a task](../approvals.html#add-an-approval-to-a-task)
- [Update an approval of a task](../approvals.html#update-an-approval-of-a-task)
- [Remove an approval from a task](../approvals.html#remove-an-approval-from-a-task)
- [Remove all approvals from a task](../approvals.html#remove-all-approvals-from-a-task)
- [Fields](../approvals.html#fields)

## List all approvals of a task

List all approvals of the [task](../../tasks.html) with a specific ID:

```
GET /tasks/:id/approvals
```

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](../approvals.html#/v1/tasks/#fields):

`status`

### Response

```
status: 200 OK
```

```
[{"approver":{"id":390,"name":"Mark Camillo","account":{"id":"wna","name":"Widget North America"}},"attachment":{"name":"workflow-1709-summary-for-mark-camillo.pdf","uri":"https://itrp.s3.amazonaws.com/attachments/workflow-1709-summary-for-mark-camillo.pdf?AWSAccessKeyId=TN5W...DR3Q&Signature=VY2t...GnT&Expires=1409976714","size":27649},"created_at":"2014-09-04T23:04:16-05:00","id":84,"planned_effort":120,"status":"assigned","updated_at":"2014-09-04T23:04:16-05:00","account":{"id":"wna","name":"Widget North America"}},{"approver":{"id":5,"name":"Howard Tanner"},"attachment":{"name":"workflow-1709-summary-for-howard-tanner.pdf","uri":"https://itrp.s3.amazonaws.com/attachments/task_approvals/workflow-1709-summary-for-howard-tanner.pdf?AWSAccessKeyId=TDRH...EO3P&Signature=WW6z...FkU&Expires=1409976714","size":26984},"created_at":"2014-09-04T23:04:16-05:00","id":85,"planned_effort":120,"status":"approved","updated_at":"2014-09-04T23:04:42-05:00"},"..."]
```

The response contains [these fields](../approvals.html#fields) by default.

## Add an approval to a task

Add an approval to a task with a specific ID.

```
POST /tasks/:id/approvals
```

When creating a new approval for a task [these fields](../approvals.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"approver":{"id":390,"name":"Mark Camillo","account":{"id":"wna","name":"Widget North America"}},"attachment":{"name":"workflow-1709-summary-for-mark-camillo.pdf","uri":"https://itrp.s3.amazonaws.com/attachments/workflow-1709-summary-for-mark-camillo.pdf?AWSAccessKeyId=TN5W...DR3Q&Signature=VY2t...GnT&Expires=1409976714","size":27649},"created_at":"2014-09-04T23:04:16-05:00","id":84,"planned_effort":120,"status":"assigned","updated_at":"2014-09-04T23:04:16-05:00","account":{"id":"wna","name":"Widget North America"}}
```

## Update an approval of a task

Update an approval of a task with a specific ID.

```
PATCH /tasks/:id/approvals/:approval_id
```

When updating an existing approval for a task [these fields](../approvals.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"status":"registered","...":"..."}
```

## Remove an approval from a task

Remove an approval with a specific ID from a task with a specific ID.

```
DELETE /tasks/:id/approvals/:approval_id
```

### Response

```
status: 204 No Content
```

## Remove all approvals from a task

Remove all approval from a task with a specific ID.

```
DELETE /tasks/:id/approvals/
```

### Response

```
status: 204 No Content
```

## Fields

approver\_id
: *Required* **[reference](../../general/data_types.html#references) to [Person](../../people.html)** — The ID of the person who is selected as the approver for the approval.

attachment
: *Readonly* **link to Workflow Summary** — The hyperlink to the Workflow Summary PDF file that was generated for the approver when the approval was last set to the status `assigned`.

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the approval was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the approval.

planned\_effort
: *Optional* **[integer](../../general/data_types.html) (max 600000)** — The Planned effort field is used to specify the number of minutes the approver is expected to spend working on the task.

status
: *Readonly* **[enum](../../general/enumerations/index.html)** — The status of the approval. Valid values are:
: - `registered`
 - `assigned`
 - `rejected`
 - `approved`
 - `canceled`

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the approval. If the approval has had no updates it contains the `created_at` value.
