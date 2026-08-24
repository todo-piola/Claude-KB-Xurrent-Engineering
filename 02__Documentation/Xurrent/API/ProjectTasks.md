# Project Tasks API

- [List project tasks](../project_tasks.html#list-project-tasks)
- [Get a single project task](../project_tasks.html#get-a-single-project-task)
- [Create a project task](../project_tasks.html#create-a-project-task)
- [Update a project task](../project_tasks.html#update-a-project-task)
- [Delete a project task](../project_tasks.html#delete-a-project-task)
- [Fields](../project_tasks.html#fields)

## List project tasks

List all project tasks for an account:

```
GET /project_tasks
```

### Response

```
status: 200 OK
```

```
[{"id":24554,"sourceID":null,"phase":{"completed_at":null,"created_at":"2016-12-23T05:09:06-06:00","id":314,"name":"Implementation","position":3,"started_at":"2016-12-23T05:09:06-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:06-06:00"},"subject":"Go-live","category":"milestone","status":"registered","completion_target_at":"2017-03-01T09:43:00-06:00","finished_at":null,"created_at":"2017-01-18T09:42:39-06:00","updated_at":"2017-01-18T09:42:39-06:00"},{"id":24553,"sourceID":null,"phase":{"completed_at":null,"created_at":"2016-12-23T05:09:06-06:00","id":314,"name":"Implementation","position":3,"started_at":"2016-12-23T05:09:06-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:06-06:00"},"subject":"Training","category":"activity","status":"in_progress","completion_target_at":"2017-03-01T09:43:00-06:00","finished_at":null,"created_at":"2017-01-18T09:42:39-06:00","updated_at":"2017-02-23T10:18:52-06:00"},"..."]
```

The response contains [these fields](../project_tasks.html#collection-fields) by default. [Filtering](../project_tasks.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of project tasks.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/project_tasks/finished`: List all finished project tasks
- `/project_tasks/open`: List all open project tasks
- `/project_tasks/managed_by_me`: List all project tasks which manager is the API user
- `/project_tasks/assigned_to_me`: List all project tasks that are assigned to the API user
- `/project_tasks/open_to_me`: List all project tasks that are assigned to the API user and which status is ‘Assigned’, ‘Accepted’, ‘In Progress’ or ‘Waiting for…’

### Collection Fields

By default the following [fields](../project_tasks.html#fields) will appear in collections of Tasks:

`id` `sourceID` `subject` `category` `status` `completion_target_at` `finished_at` `created_at` `updated_at`

Obtain a different set of [fields](../project_tasks.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../project_tasks.html#fields):

`id` `source` `sourceID` `subject` `category` `status` `completion_target_at` `finished_at` `created_at` `updated_at`

### Sorting

By default a collection of project tasks is sorted **descending** by `id`.

The following [fields](../project_tasks.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `category` `status` `completion_target_at` `finished_at` `created_at` `updated_at`

### Response

The response is similar to the response in [List project tasks](../project_tasks.html#list-project-tasks)

## Get a single project task

```
GET /project_tasks/:id
```

### Response

```
status: 200 OK
```

```
{"anticipated_assignment_at":"2017-02-23T09:43:00-06:00","assigned_at":"2017-02-23T09:04:17-06:00","attachments":[],"category":"activity","completion_target_at":"2017-03-01T09:43:00-06:00","created_at":"2017-01-18T09:42:39-06:00","custom_fields":null,"deadline":null,"finished_at":null,"id":24553,"instructions":"Conduct the training for all participants.","manager":{"id":156,"name":"Ellen Brown","account":{"id":"widget","name":"Widget International"}},"phase":{"completed_at":null,"created_at":"2016-12-23T05:09:06-06:00","id":314,"name":"Implementation","position":3,"started_at":"2016-12-23T05:09:06-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:06-06:00"},"planned_duration":1920,"project":{"id":4021,"subject":"Best in Customer Satisfaction (BICS)"},"required_approvals":null,"source":null,"sourceID":null,"start_at":null,"status":"in_progress","subject":"Training","supplier":null,"supplier_requestID":null,"template":{"id":822,"subject":"Training"},"updated_at":"2017-02-23T10:18:52-06:00","urgent":false,"waiting_until":null}
```

The response contains [these fields](../project_tasks.html#fields).

## Create a Project Task

```
POST /projects/:project_id/tasks
```

When creating a new project task [these fields](../project_tasks.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"anticipated_assignment_at":"...","...":"..."}
```

The response contains [all fields](../project_tasks.html#fields) of the created project task and is similar to the response in [Get a single project task](../project_tasks.html#get-a-single-project-task)

### Predecessors and Successors

When a new project task is added to an existing project, it can be inserted at any position in the project’s workflow. To do this, the predecessor(s) and successor(s) can be specified for the new project task. The following is a CURL example for creating a new project task with two predecessor relations and one successor relation:

```
$ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X POST \
 -d '{"subject":"Perform extra manual test","category":"implementation","planned_duration":600,"team_id":128,"impact":"none","predecessor_ids":[24551,24552],"successor_ids":[24554]}' \
 https://api.xurrent.com/v1/projects/4021/project_tasks
```

## Update a Project Task

```
PATCH /project_tasks/:id
```

When updating a project task [these fields](../project_tasks.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"anticipated_assignment_at":"...","...":"..."}
```

The response contains [all fields](../project_tasks.html#fields) of the updated project task and is similar to the response in [Get a single project task](../project_tasks.html#get-a-single-project-task)

## Delete a Project Task

```
DELETE /project_tasks/:id
```

### Response

```
status: 204 No Content
```

## Fields

agile\_board
: *Optional* **[reference](../general/data_types.html#references) to [Agile Board](../agile_boards/index.html)** — The Agile board on which the project task is placed.

agile\_board\_column
: *Optional* **[reference](../general/data_types.html#references) to [Agile Board Column](../agile_boards/columns.html)** — The column of the agile board on which the project task is placed.

agile\_board\_column\_position
: *Optional* **[integer](../general/data_types.html)** — The Position field is used to specify the position of the project task,
 relative to the other items within the column of the agile board. The topmost item has position 1.

anticipated\_assignment\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Anticipated assignment field shows the date and time at which the project task is currently expected to be assigned.

assigned\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Assigned field is automatically set to the current date and time when the project task is assigned.

attachments
: *Readonly* **aggregated Attachments**
: Use [Project tasks - Notes API](notes/index.html) to get note attachments.

category
: *Required* **[enum](../general/enumerations/index.html)** — The Category field is used to select the category of the project task. Activity tasks are used to assign project-related work to people. Approval tasks are used to collect approvals for projects. Milestones are used to mark specific points along a project’s implementation plan. Valid values are:
: - `activity`: Activity
 - `approval`: Approval
 - `milestone`: Milestone

checked\_items
: *Optional* **array of string** — The names of the checklist items that are checked within the instructions field.

completion\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Completion target field shows the date and time at which the project task is expected to be completed.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the project task was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the project task template that was used to register the project task.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

deadline
: *Optional* **[datetime](../general/data_types.html)** — The Deadline field is used to specify the date and time at which the milestone needs to have been reached.

finished\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Finished field is automatically set to the date and time at which the project task is saved with the status “Failed”, “Rejected”, “Completed”, “Approved” or “Canceled”.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the project task.

instructions
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Instructions field is used to provide instructions for the person(s) to whom the project task will be assigned.

instructions\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Instructions field.

manager
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field shows the person who is selected in the Manager field of the project that this project task belongs to.

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to provide information for the person to whom the project task is assigned. It is also used to provide a summary of the actions that have been taken to date and the results of these actions.
: The Note field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Note field.

phase
: *Readonly* **[reference](../general/data_types.html#references) to [Phase](../projects/phases.html)** — The Phase field is used to select the phase of the project to which the project task belongs.

planned\_duration
: *Required* **[integer](../general/data_types.html) (max 600000)** — The Planned duration field is used to enter the number of minutes it is expected to take for the project task to be completed following its assignment, or following its fixed start date and time if the Start no earlier than field is filled out.

planned\_effort
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field is used to specify the number of minutes the team is expected to spend working on the project task.

project
: *Required* **[reference](../general/data_types.html#references) to [Project](../projects/index.html)** — The Project field shows the ID and subject of the project to which the project task belongs.

required\_approvals
: *Optional* **[integer](../general/data_types.html)**, default: `1` — The Required approvals field is used to specify the number of assignees who need to have provided their approval before the status of the project task gets updated to “Approved”.

resolution\_duration
: *Readonly* **[integer](../general/data_types.html)** — The number of minutes it took to complete this problem, which is calculated as the difference between the `assigned_at` and `finished_at` values.

skill\_pool
: *Optional* **[reference](../general/data_types.html#references) to [Skill Pool](../skill_pools/index.html)** — The Skill Pool field is used to select the skill pool to whom the project task is to be assigned.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_at
: *Optional* **[datetime](../general/data_types.html)** — The Start no earlier than field is only used when work on the project task may not start before a specific date and time.

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `registered` — The Status field is used to select the current status of the project task. Valid values are:
: - `registered`: Registered
 - `assigned`: Assigned
 - `accepted`: Accepted
 - `in_progress`: In Progress
 - `waiting_for`: Waiting for…
 - `failed`: Failed
 - `rejected`: Rejected
 - `completed`: Completed
 - `approved`: Approved
 - `canceled`: Canceled

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the objective of the project task.

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the supplier organization that has been asked to assist with the completion of the project task.

supplier\_requestID
: *Optional* **[string](../general/data_types.html) (max 255)** — The Supplier request ID field is used to enter the identifier under which the request to help with the execution of the project task has been registered at the supplier organization.

team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Team field is used to select the [Team](../teams.html) to which the project task is to be assigned.

template
: *Required* **[reference](../general/data_types.html#references) to [Task Template](../task_templates.html)** — The Template field contains the link to the project task template that was used to register the project task.

time\_spent
: *Optional* **[integer](../general/data_types.html)** — The Time spent field is used to enter the time that you have spent working on the project task since you started to work on it or, if you already entered some time for this project task, since you last added your time spent in it.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

time\_spent\_effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The Effort class field is used to select the effort class that best reflects the type of effort for which time spent is being registered.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the project task. If the project task has no updates it contains the `created_at` value.

urgent
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The project task can be marked as urgent by setting the Urgent field to `true`.

waiting\_until
: *Optional* **[datetime](../general/data_types.html)** — The Waiting until field is used to specify the date and time at which the status of the project task is to be updated from `waiting_for` to `assigned`. This field is available only when the Status field is set to `waiting_for`.
: The Waiting until field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

work\_hours\_are\_24x7
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — When set to true, the completion target of the project task is calculated using a 24x7 calendar rather than normal business hours.
