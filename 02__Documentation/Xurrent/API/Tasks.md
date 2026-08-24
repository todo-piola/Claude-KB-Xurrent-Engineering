# Tasks API

- [List tasks](../tasks.html#list-tasks)
- [Get a single task](../tasks.html#get-a-single-task)
- [Create a task](../tasks.html#create-a-task)
- [Update a task](../tasks.html#update-a-task)
- [Fields](../tasks.html#fields)

## List tasks

List all tasks for an account:

```
GET /tasks
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:14:17-06:00","category":"implementation","finished_at":null,"sourceID":null,"updated_at":"2016-03-14T03:14:17-06:00","member":{"name":"Barney Turban","id":58},"subject":"Inform approvers and requesters of the completion of the workflow","id":95,"impact":"none","team":{"name":"Windows Servers","id":14},"status":"registered","completion_target_at":"2016-03-15T16:33:00-06:00"},"..."]
```

The response contains [these fields](../tasks.html#collection-fields) by default. [Filtering](../tasks.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of tasks.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/tasks/finished`: List all finished tasks
- `/tasks/open`: List all open tasks
- `/tasks/managed_by_me`: List all tasks that are part of a workflow which manager is the API user
- `/tasks/assigned_to_my_team`: List all tasks that are assigned to one of the teams that the API user is a member of
- `/tasks/assigned_to_me`: List all tasks that are assigned to the API user
- `/tasks/approval_by_me`: List all approval tasks that are assigned to the API user and which status in different from ‘Registered’

### Collection Fields

By default the following [fields](../tasks.html#fields) will appear in collections of tasks:

`id` `sourceID` `subject` `impact` `category` `status` `team` `member` `completion_target_at` `finished_at` `created_at` `updated_at`

Obtain a different set of [fields](../tasks.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../tasks.html#fields):

`id` `source` `sourceID` `subject` `impact` `category` `status` `team` `member`
`completion_target_at` `finished_at` `created_at` `updated_at` `template` `workflow`

### Sorting

By default a collection of tasks is sorted **descending** by `id`.

The following [fields](../tasks.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `impact` `category` `status` `team` `member` `completion_target_at` `finished_at` `created_at` `updated_at`

### Response

The response is similar to the response in [List tasks](../tasks.html#list-tasks)

## Get a single task

```
GET /tasks/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2016-03-14T03:14:13-06:00","category":"approval","sourceID":null,"finished_at":"2009-02-04T08:51:00-06:00","anticipated_assignment_at":null,"updated_at":"2016-03-14T03:14:13-06:00","supplier":null,"new_assignment":false,"member":null,"manager":{"name":"Carla Cluster","id":54},"instructions":null,"assigned_at":"2009-02-03T03:08:00-06:00","workflow":{"id":238,"subject":"Install new rack"},"supplier_requestID":null,"subject":"Service owner approval and floor space assignment for new rack","start_at":null,"id":2,"planned_duration":720,"planned_effort":null,"required_approvals":3,"impact":null,"team":null,"status":"approved","source":"4me","completion_target_at":null,"template":{"id":28,"subject":"Service owner approval"},"custom_fields":null,"waiting_until":null}
```

The response contains [these fields](../tasks.html#fields).

## Create a task

```
POST /workflows/:workflow_id/tasks
```

When creating a new task [these fields](../tasks.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"anticipated_assignment_at":"...","...":"..."}
```

The response contains [all fields](../tasks.html#fields) of the created task and is similar to the response in [Get a single task](../tasks.html#get-a-single-task)

### Predecessors and Successors

When a new task is added to an existing workflow, it can be inserted at any position in the workflow. To do this, the predecessor(s) and successor(s) can be specified for the new task. The following is a CURL example for creating a new task with two predecessor relations and one successor relation:

```
$ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X POST \
 -d '{"subject":"Perform extra manual test","category":"implementation","planned_duration":600,"team_id":128,"impact":"none","predecessor_ids":[21126,21127],"successor_ids":[21128]}' \
 https://api.xurrent.com/v1/workflows/5694/tasks
```

## Update a task

```
PATCH /tasks/:id
```

When updating a task [these fields](../tasks.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"anticipated_assignment_at":"...","...":"..."}
```

The response contains [all fields](../tasks.html#fields) of the updated task and is similar to the response in [Get a single task](../tasks.html#get-a-single-task)

## Fields

agile\_board
: *Optional* **[reference](../general/data_types.html#references) to [Agile Board](../agile_boards/index.html)** — The Agile board on which the task is placed.

agile\_board\_column
: *Optional* **[reference](../general/data_types.html#references) to [Agile Board Column](../agile_boards/columns.html)** — The column of the agile board on which the task is placed.

agile\_board\_column\_position
: *Optional* **[integer](../general/data_types.html)** — The Position field is used to specify the position of the task,
 relative to the other items within the column of the agile board. The topmost item has position 1.

anticipated\_assignment\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Anticipated assignment field shows the date and time at which the task is currently expected to be assigned.

assigned\_at
: *Optional* **[datetime](../general/data_types.html)** — The Assigned field is automatically set to the current date and time when the task is assigned.

attachments
: *Readonly* **aggregated Attachments**
: Use [Tasks - Notes API](notes/index.html) to get note attachments.

category
: *Required* **[enum](../general/enumerations/index.html)** — The Category field is used to select the category of the task. Risk & impact tasks are used to help plan workflows. Approval tasks are used to collect approvals for workflows. These can be used at various stages in the life of the workflow. Implementation tasks are added to workflows for development, installation, configuration, test, transfer and administrative work that needs to be completed for the implementation of the workflow. Valid values are:
: - `risk_and_impact`: Risk & Impact
 - `approval`: Approval
 - `implementation`: Implementation
 - `automation`: Automation

checked\_items
: *Optional* **array of string** — The names of the checklist items that are checked within the instructions field.

completion\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Completion target field shows the date and time at which the task is expected to be completed.

copy\_note\_to\_request
: *Optional* **[boolean](../general/data_types.html)** — When set to `true`, notes on this task are copied as public notes to the request of the task’s workflow. Defaults to the value set on the task’s template.

copy\_note\_to\_workflow
: *Optional* **[boolean](../general/data_types.html)** — When set to `true`, notes on this task are copied to the task’s workflow. Defaults to the value set on the task’s template.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the task was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the task template that was used to register the task.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

failure\_task
: *Optional* **[reference](../general/data_types.html#references) to [Task](../tasks.html)** — The task that will be assigned in case this task is failed or rejected.

finished\_at
: *Optional* **[datetime](../general/data_types.html)** — The Finished field is automatically set to the date and time at which the task is saved with the status “Failed”, “Rejected”, “Completed”, “Approved” or “Canceled”.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the task.

impact
: *Optional* **[enum](../general/enumerations/index.html)** — The Impact field is used to select the extent to which the [Service Instances](../service_instances/index.html) related to the task will be impacted by the completion of the task. Valid values are:
: - `none`: None - Service Not Degraded
 - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

instructions
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Instructions field is used to provide instructions for the person to whom the task will be assigned.

instructions\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Instructions field.

manager
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field shows the person who is selected in the Manager field of the workflow that this task belongs to.

member
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Member field is used to select the person to whom the task is to be assigned. This field’s value is `null` in case of an approval task with multiple approvers (see [Approvals](approvals.html)).

new\_assignment
: *Readonly* **[boolean](../general/data_types.html)** — default: `false`

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to provide information for the person to whom the task is assigned. It is also used to provide a summary of the actions that have been taken to date and the results of these actions.
: The Note field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Note field.

phase
: *Optional* **[reference](../general/data_types.html#references) to [Phase](../workflows/phases.html)** — The Phase field is used to select the phase of the workflow to which the task belongs.

planned\_duration
: *Required* **[integer](../general/data_types.html) (max 600000)** — The Planned duration field is used to enter the number of minutes it is expected to take for the task to be completed following its assignment, or following its fixed start date and time if the Start no earlier than field is filled out.

planned\_effort
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field is used to specify the number of minutes the member is expected to spend working on the task.

provider\_not\_accountable
: *Readonly* **[boolean](../general/data_types.html)** — The Provider not accountable field value is used to indicate whether the provider is not to be accountable for the affected SLAs linked to the requests that are linked to the workflow of the task, as long as the task is active.

rejection\_count
: *Readonly* **[integer](../general/data_types.html)** — The Rejection count field is incremented on (each) rejection of an approval task.

request
: *Optional* **[reference](../general/data_types.html#references) to [Request](../requests.html)** — The Request field is visible only after a request has been generated by the task. This field shows the [Request](../requests.html) that was generated. As soon as this request has been completed with the completion reason “Solved”, the task’s status is set to “Completed”.

request\_template
: *Optional* **[reference](../general/data_types.html#references) to [Request Template](../request_templates.html)** — The Request template field is used to select the [Request template](../request_templates.html) that must be used to generate a new request when the status of the task is set to “Assigned”, “Accepted” or “In Progress”.

request\_service\_instance
: *Optional* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The Service instance field is used to select the [Service instance](../service_instances/index.html) that must be applied to the new request that is generated when the status of the task is set to “Assigned”, “Accepted” or “In Progress”.

required\_approvals
: *Optional* **[integer](../general/data_types.html)**, default: `1` — The Required approvals field is used in approval tasks to specify the number of approvers who need to have provided their approval before the status of the task gets updated to “Approved”.

resolution\_duration
: *Readonly* **[integer](../general/data_types.html)** — The number of minutes it took to complete this problem, which is calculated as the difference between the `assigned_at` and `finished_at` values.

skill\_pool
: *Optional* **[reference](../general/data_types.html#references) to [Skill Pool](../skill_pools/index.html)** — The Skill Pool field is used to select the skill pool to whom the task is to be assigned.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_at
: *Optional* **[datetime](../general/data_types.html)** — The Start no earlier than field is only used when work on the task may not start before a specific date and time.

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `registered` — The Status field is used to select the current status of the task. Valid values are:
: - `registered`: Registered
 - `declined`: Declined
 - `assigned`: Assigned
 - `accepted`: Accepted
 - `in_progress`: In Progress
 - `waiting_for`: Waiting for…
 - `waiting_for_customer`: Waiting for Customer
 - `request_pending`: Request Pending
 - `failed`: Failed
 - `rejected`: Rejected
 - `completed`: Completed
 - `approved`: Approved
 - `canceled`: Canceled

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the objective of the task.

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the supplier organization that has been asked to assist with the completion of the task.

supplier\_requestID
: *Optional* **[string](../general/data_types.html) (max 255)** — The Supplier request ID field is used to enter the identifier under which the request to help with the execution of the task has been registered at the supplier organization.

team
: *Required* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Team field is used to select the [Team](../teams.html) to which the task is to be assigned.

template
: *Required* **[reference](../general/data_types.html#references) to [Task Template](../task_templates.html)** — The Template field contains the link to the task template that was used to register the task.

time\_spent
: *Optional* **[integer](../general/data_types.html)** — The Time spent field is used to enter the time that you have spent working on the task since you started to work on it or, if you already entered some time for this task, since you last added your time spent in it.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

time\_spent\_effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The Effort class field is used to select the effort class that best reflects the type of effort for which time spent is being registered.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the task. If the task has no updates it contains the `created_at` value.

urgent
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — When the task has been marked as urgent, the Urgent field is set to `true`.

waiting\_until
: *Optional* **[datetime](../general/data_types.html)** — The Waiting until field is used to specify the date and time at which the status of the task is to be updated from `waiting_for` to `assigned`. This field is available only when the Status field is set to `waiting_for`.

work\_hours\_are\_24x7
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — When set to true, the completion target of the task is calculated using a 24x7 calendar rather than normal business hours.

workflow
: *Required* **[reference](../general/data_types.html#references) to [Workflow](../workflows.html)** — The Workflow field shows the ID and subject of the workflow to which the task belongs.
