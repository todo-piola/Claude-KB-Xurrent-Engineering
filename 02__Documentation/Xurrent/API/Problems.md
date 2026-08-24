# Problems API

- [List problems](../problems.html#list-problems)
- [Get a single problem](../problems.html#get-a-single-problem)
- [Create a problem](../problems.html#create-a-problem)
- [Update a problem](../problems.html#update-a-problem)
- [Archive a problem](../problems.html#archive-a-problem)
- [Trash a problem](../problems.html#trash-a-problem)
- [Restore a problem](../problems.html#restore-a-problem)
- [Fields](../problems.html#fields)

## List problems

List all problems for an account:

```
GET /problems
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-13T10:27:00-06:00","analysis_target_at":"2016-03-20T03:00:00-06:00","sourceID":null,"updated_at":"2016-03-14T03:14:13-06:00","service":{"name":"Expense Reporting","id":14,"provider":{"name":"Widget Data Center, External IT","id":30}},"member":{"name":"Tom Waters","id":36},"solved_at":null,"subject":"Clicking on the Submit button does not submit new expense report","id":221,"impact":"top","team":{"name":"Application Development","id":7},"status":"in_progress"},"..."]
```

The response contains [these fields](../problems.html#collection-fields) by default. [Filtering](../problems.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of problems.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/problems/active`: List all active problems
- `/problems/known_errors`: List all known\_errors problems
- `/problems/progress_halted`: List all progress\_halted problems
- `/problems/solved`: List all solved problems
- `/problems/managed_by_me`: List all problems which manager is the API user
- `/problems/assigned_to_my_team`: List all problems that are assigned to one of the teams that the API user is a member of
- `/problems/assigned_to_me`: List all problems that are assigned to the API user

### Collection Fields

By default the following [fields](../problems.html#fields) will appear in collections of problems:

`id` `sourceID` `subject` `impact` `status` `known_error` `analysis_target_at` `solved_at` `team` `member` `service` `created_at` `updated_at`

Obtain a different set of [fields](../problems.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../problems.html#fields):

`id` `source` `sourceID` `subject` `impact` `service` `status` `analysis_target_at` `solved_at` `created_at` `updated_at`

### Sorting

By default a collection of problems is sorted **descending** by `id`.

The following [fields](../problems.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `impact` `status` `known_error` `analysis_target_at` `solved_at` `team` `member` `service` `created_at` `updated_at`

### Response

The response is similar to the response in [List problems](../problems.html#list-problems)

## Get a single problem

```
GET /problems/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2016-02-03T14:49:00-05:00","category":"proactive","analysis_target_at":null,"sourceID":null,"updated_at":"2016-03-14T03:14:12-06:00","supplier":null,"service":{"name":"Windows Server","id":33,"provider":{"name":"Widget Data Center, External IT","id":30}},"new_assignment":true,"known_error":false,"solved_at":null,"member":{"name":"Barney Turban","id":58},"manager":{"name":"Frank Watson","id":32},"supplier_requestID":null,"subject":"Insufficient memory warnings for Sales Tracking Production","id":208,"workflow":null,"project":null,"knowledge_article":null,"workaround":null,"impact":"none","team":{"name":"Windows Servers","id":14},"status":"change_requested","source":null,"waiting_until":null}
```

The response contains [these fields](../problems.html#fields).

## Create a problem

```
POST /problems
```

When creating a new problem [these fields](../problems.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"analysis_target_at":"...","...":"..."}
```

The response contains [all fields](../problems.html#fields) of the created problem and is similar to the response in [Get a single problem](../problems.html#get-a-single-problem)

## Update a problem

```
PATCH /problems/:id
```

When updating a problem [these fields](../problems.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"analysis_target_at":"...","...":"..."}
```

The response contains [all fields](../problems.html#fields) of the updated problem and is similar to the response in [Get a single problem](../problems.html#get-a-single-problem)

## Archive a problem

```
POST /problems/:id/archive
```

Moves a given problem to the [Archive](../archive/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the problem.

### Response

```
status: 200 OK
```

```
{"archived":"true","analysis_target_at":"...","...":"..."}
```

The response contains [all fields](../problems.html#fields) of the archived problem and is similar to the response in [Get a single problem](../problems.html#get-a-single-problem)

## Trash a problem

```
POST /problems/:id/trash
```

Moves a given problem to the [Trash](../trash/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the problem.

### Response

```
status: 200 OK
```

```
{"trashed":"true","analysis_target_at":"...","...":"..."}
```

The response contains [all fields](../problems.html#fields) of the archived problem and is similar to the response in [Get a single problem](../problems.html#get-a-single-problem)

## Restore a problem

```
POST /problems/:id/restore
```

Moves a given problem from the [Archive](../archive/index.html) or the [Trash](../trash/index.html) back into the view of “Solved Problems”.
This action requires the Account Administrator or Directory Administrator role in the account of the problem.

### Response

```
status: 200 OK
```

```
{"analysis_target_at":"...","...":"..."}
```

The response contains [all fields](../problems.html#fields) of the archived problem and is similar to the response in [Get a single problem](../problems.html#get-a-single-problem)

## Fields

agile\_board
: *Optional* **[reference](../general/data_types.html#references) to [Agile Board](../agile_boards/index.html)** — The Agile board on which the problem is placed.

agile\_board\_column
: *Optional* **[reference](../general/data_types.html#references) to [Agile Board Column](../agile_boards/columns.html)** — The column of the agile board on which the problem is placed.

agile\_board\_column\_position
: *Optional* **[integer](../general/data_types.html)** — The Position field is used to specify the position of the problem,
 relative to the other items within the column of the agile board. The topmost item has position 1.

analysis\_target\_at
: *Optional* **[datetime](../general/data_types.html)** — The Analysis target field is used to specify when the current assignee needs to have completed the root cause analysis of the problem.

attachments
: *Readonly* **aggregated Attachments**
: Use [Problems - Notes API](notes/index.html) to get note attachments.

category
: *Optional* **[enum](../general/enumerations/index.html)**, default: `reactive` — The Category field is used to select the category of the problem. Valid values are:
: - `reactive`: Reactive - Existing Problem
 - `proactive`: Proactive - Anticipated Problem

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the problem was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the problem.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the problem.

impact
: *Required* **[enum](../general/enumerations/index.html)** — The Impact field is used to select the extent to which the service is impacted when an incident occurs that is caused by the problem. Valid values are:
: - `none`: None - Does Not Degrade Service
 - `low`: Low - Degrades Service for One User
 - `medium`: Medium - Brings Service Down for One User
 - `high`: High - Degrades Service for Several Users
 - `top`: Top - Brings Service Down for Several Users

knowledge\_article
: *Optional* **[reference](../general/data_types.html#references) to [Knowledge Article](../knowledge_articles.html)** — The Knowledge article field is used to select the [knowledge article](../knowledge_articles.html) which instructions should be followed to resolve incidents caused by this problem until a structural solution has been implemented.

known\_error
: *Optional* **[boolean](../general/data_types.html)** — The Known error box is checked when the underlying cause of the problem has been found and a temporary workaround has been proposed.

manager
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field is used to select the [Person](../people.html) who is responsible for coordinating the problem through root cause analysis, the proposal of a structural solution and ultimately its closure.

member
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Member field is used to select the person to whom the problem is to be assigned.

new\_assignment
: *Readonly* **[boolean](../general/data_types.html)** — default: `true`

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to provide a detailed description of the symptoms that are caused by the problem.
: The Note field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Note field.

planned\_effort
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field is used to specify the number of minutes the member is expected to spend working on the problem.

product\_backlog
: *Optional* **[reference](../general/data_types.html#references) to [Product Backlog](../product_backlogs/index.html)** — The Product backlog field is used to place the problem on a product backlog. When a problem is placed on a product backlog without specifying a `product_backlog_position` it is placed at the bottom of the product backlog.

product\_backlog\_position
: *Optional* **[integer](../general/data_types.html)** — The Product backlog position field is used to determine the relative position of the problem on the product backlog (the top most item has position 1). When a problem is placed on a product backlog without specifying a `product_backlog_position` it is placed at the bottom of the product backlog.

project
: *Optional* **[reference](../general/data_types.html#references) to [Project](../projects/index.html)** — The Project field is used to link the problem to a project.

resolution\_duration
: *Readonly* **[integer](../general/data_types.html)** — The number of minutes it took to complete this problem, which is calculated as the difference between the `created_at` and `solved_at` values.

service
: *Required* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the service in which instance(s) the problem resides.

solved\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Solved at field is automatically set to the date and time at which the problem is saved with the status “Solved”.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `assigned` — The Status field is used to select the current status of the problem. Valid values are:
: - `declined`: Declined
 - `assigned`: Assigned
 - `accepted`: Accepted
 - `in_progress`: In Progress
 - `waiting_for`: Waiting for…
 - `analyzed`: Analyzed
 - `change_requested`: Change Requested
 - `workflow_pending`: Workflow Pending
 - `on_backlog`: On Backlog
 - `project_pending`: Project Pending
 - `progress_halted`: Progress Halted
 - `solved`: Solved

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the symptoms that the problem causes.

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the supplier organization that has been asked for a solution to the problem.

supplier\_requestID
: *Optional* **[string](../general/data_types.html) (max 255)**

team
: *Required* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Team field is used to select the [Team](../teams.html) to which the problem is to be assigned. After a service has been selected in the Service field, the support team of the service is automatically selected in this field.

time\_spent
: *Optional* **[integer](../general/data_types.html)** — The Time spent field is used to enter the time that you have spent working on the problem since you started to work on it or, if you already entered some time for this problem, since you last added your time spent in it.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

time\_spent\_effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The Effort class field is used to select the effort class that best reflects the type of effort for which time spent is being registered.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the problem.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the problem. If the problem has no updates it contains the `created_at` value.

urgent
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — When the problem has been marked as urgent, the Urgent field is set to `true`.

waiting\_until
: *Optional* **[datetime](../general/data_types.html)** — The Waiting until field is used to specify the date and time at which the status of the problem is to be updated from `waiting_for` to `assigned`. This field is available only when the Status field is set to `waiting_for`.

workaround
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Workaround field is used to describe the temporary workaround that should be applied to resolve incidents caused by this problem until a structural solution has been implemented.

workaround\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Workaround field.

workflow
: *Optional* **[reference](../general/data_types.html#references) to [Workflow](../workflows.html)** — The Workflow field is used to relate the problem to the [Workflow](../workflows.html) that will implement the proposed permanent solution for the problem.
