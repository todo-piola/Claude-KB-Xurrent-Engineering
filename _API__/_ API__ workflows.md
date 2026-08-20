# Workflows API

- [List workflows](../workflows.html#list-workflows)
- [Get a single workflow](../workflows.html#get-a-single-workflow)
- [Create a workflow](../workflows.html#create-a-workflow)
- [Update a workflow](../workflows.html#update-a-workflow)
- [Archive a workflow](../workflows.html#archive-a-workflow)
- [Trash a workflow](../workflows.html#trash-a-workflow)
- [Restore a workflow](../workflows.html#restore-a-workflow)
- [Fields](../workflows.html#fields)

## List workflows

List all workflows for an account:

```
GET /workflows
```

### Response

```
status: 200 OK
```

```
[{"completed_at":null,"created_at":"2016-03-10T12:32:00-06:00","category":"standard","sourceID":null,"updated_at":"2016-03-14T03:14:17-06:00","service":{"id":21,"name":"Email","localized_name":"Email","provider":{"name":"Widget Data Center, External IT","id":44,"account":{"id":"widget","name":"Widget International"}}},"manager":{"id":37,"name":"Barney Turban","account":{"id":"widget","name":"Widget International"}},"subject":"Upgrade Email servers to Exchange Server 2007 SP2","id":1686,"impact":"top","status":"risk_and_impact","completion_target_at":"2016-03-15T16:33:00-06:00"},"..."]
```

The response contains [these fields](../workflows.html#collection-fields) by default. [Filtering](../workflows.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of workflows.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/workflows/completed`: List all completed workflows
- `/workflows/open`: List all open workflows
- `/workflows/managed_by_me`: List all workflows which manager is the API user

### Collection Fields

By default the following [fields](../workflows.html#fields) will appear in collections of workflows:

`id` `sourceID` `subject` `manager` `category` `impact` `status` `completion_target_at` `completed_at` `service` `created_at` `updated_at`

Obtain a different set of [fields](../workflows.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../workflows.html#fields):

`id` `source` `sourceID` `subject` `manager` `category` `impact` `status` `completion_target_at`
`completed_at` `service` `created_at` `updated_at` `template` `start_at` `project` `release`

### Sorting

By default a collection of workflows is sorted **descending** by `id`.

The following [fields](../workflows.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `manager` `category` `impact` `status` `completion_target_at` `completed_at` `service` `created_at` `updated_at`

### Response

The response is similar to the response in [List workflows](../workflows.html#list-workflows)

## Get a single workflow

```
GET /workflows/:id
```

### Response

```
status: 200 OK
```

```
{"completion_reason":"complete","completed_at":"2016-03-14T03:14:13-06:00","created_at":"2009-02-03T03:08:00-06:00","category":"standard","sourceID":null,"updated_at":"2016-03-14T03:14:13-06:00","release":null,"project":null,"service":{"name":"Rack Space","id":26,"provider":{"name":"Widget Data Center, External IT","id":44}},"manager":{"id":77,"name":"Carla Cluster","account":{"id":"widget","name":"Widget International"}},"subject":"Install new rack","start_at":"2016-03-14T09:14:13Z","id":238,"justification":"expansion","impact":"none","status":"completed","source":"4me","workflow_type":"infrastructure_change","completion_target_at":null,"template":{"id":37,"subject":"Non-standard infrastructure change"},"custom_fields":null}
```

The response contains [these fields](../workflows.html#fields).

## Create a workflow

```
POST /workflows
```

When creating a new workflow [these fields](../workflows.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](../workflows.html#fields) of the created workflow and is similar to the response in [Get a single workflow](../workflows.html#get-a-single-workflow)

## Update a workflow

```
PATCH /workflows/:id
```

When updating a workflow [these fields](../workflows.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](../workflows.html#fields) of the updated workflow and is similar to the response in [Get a single workflow](../workflows.html#get-a-single-workflow)

## Archive a workflow

```
POST /workflows/:id/archive
```

Moves a given workflow to the [Archive](../archive/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the workflow.

### Response

```
status: 200 OK
```

```
{"archived":"true","analysis_target_at":"...","...":"..."}
```

The response contains [all fields](../workflows.html#fields) of the archived workflow and is similar to the response in [Get a single workflow](../workflows.html#get-a-single-workflow)

## Trash a workflow

```
POST /workflows/:id/trash
```

Moves a given workflow to the [Trash](../trash/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the workflow.

### Response

```
status: 200 OK
```

```
{"trashed":"true","analysis_target_at":"...","...":"..."}
```

The response contains [all fields](../workflows.html#fields) of the archived workflow and is similar to the response in [Get a single workflow](../workflows.html#get-a-single-workflow)

## Restore a workflow

```
POST /workflows/:id/restore
```

Moves a given workflow from the [Archive](../archive/index.html) or the [Trash](../trash/index.html) back into the view of “Completed Workflows”.
This action requires the Account Administrator or Directory Administrator role in the account of the workflow.

### Response

```
status: 200 OK
```

```
{"analysis_target_at":"...","...":"..."}
```

The response contains [all fields](../workflows.html#fields) of the archived workflow and is similar to the response in [Get a single workflow](../workflows.html#get-a-single-workflow)

## Fields

actual\_effort
: *Readonly* **[integer](../general/data_types.html)** — The Actual effort field shows the total time that has already been spent on the workflow. This is the sum of the time spent on each of the workflow’s tasks and the planned effort of the related requests and problems.

actual\_vs\_planned\_effort\_percentage
: *Readonly* **[integer](../general/data_types.html)** — The actual effort as a percentage of the planned effort.

attachments
: *Readonly* **aggregated Attachments**
: Use [Workflows - Notes API](notes/index.html) to get note attachments.

category
: *Required* **[enum](../general/enumerations/index.html)** — The Category field is used to select the category of the workflow. A workflow is either planned or unplanned. Select the category “Emergency” for workflows that were not planned. Workflows that were planned by applying a standard workflow template are automatically set to the category “Standard”. When a workflow template is used that is not approved as a standard workflow, then the option “Non-Standard” is automatically selected in this field. Valid values are:
: - `standard`: Standard - Approved Workflow Template Was Used
 - `non_standard`: Non-Standard - Approved Workflow Template Not Available
 - `emergency`: Emergency - Required for Incident Resolution
 - `order`: Order - Organization Order Workflow

completed\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Completed at field is automatically set to the date and time at which the workflow is saved with the status “Completed”.

completion\_reason
: *Optional* **[enum](../general/enumerations/index.html)** — The Completion reason field is used to select the appropriate completion reason for the workflow when it has been completed. It is automatically set to “Complete” when all tasks related to the workflow have reached the status “Completed”, “Approved” or “Canceled”. Valid values are:
: - `withdrawn`: Withdrawn - Withdrawn by Requester
 - `rejected`: Rejected - Rejected by Approver
 - `rolled_back`: Rolled Back - Original Environment Restored
 - `failed`: Failed - No Requirements Met
 - `partial`: Partial - Not All Requirements Met
 - `disruptive`: Disruptive - Caused Service Disruption
 - `complete`: Complete - All Requirements Met

completion\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Completion target field shows the target date and time of the last task of the workflow.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the workflow was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the related workflow template.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the workflow.

impact
: *Readonly* **[enum](../general/enumerations/index.html)**, default: `none` — The Impact field shows the maximum impact level that is selected in the tasks that are a part of the workflow. This indicates the maximum extent to which the service is impacted when the implementation tasks that are related to the workflow are executed. Valid values are:
: - `none`: None - Service Not Degraded
 - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

justification
: *Required* **[enum](../general/enumerations/index.html)** — The Justification field is used to select the reason why the workflow was requested. Valid values are:
: - `compliance`: Compliance
 - `correction`: Correction
 - `expansion`: Expansion
 - `improvement`: Improvement
 - `maintenance`: Maintenance
 - `move`: Move
 - `removal`: Removal
 - `replacement`: Replacement
 - `purchase`: Purchase

manager
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field is used to select the [Person](../people.html) who is responsible for coordinating the implementation of the workflow. If a manager is not specified for a new workflow, the API user is selected in the Manager field by default.

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to provide a high-level description of the result that should be accomplished by the implementation of the workflow. It is also used to add any information that could prove useful for anyone affected by the workflow, including the people whose approval is needed and the specialists who are helping to implement it.
: The Note field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Note field.

prevent\_request\_completion
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether permissions to complete linked requests are restricted.

planned\_effort
: *Readonly* **[integer](../general/data_types.html)** — The Planned effort field shows the total planned effort of the workflow. This is the sum of the planned effort (or planned duration if the planned effort is empty) of the workflow’s tasks and the planned effort of the related requests and problems.

project
: *Optional* **[reference](../general/data_types.html#references) to [Project](../projects/index.html)** — The Project field is used to link the workflow to a project.

release
: *Optional* **[reference](../general/data_types.html#references) to [Release](../releases.html)** — The Release field is used to select the release that the workflow is a part of.

resolution\_duration
: *Readonly* **[integer](../general/data_types.html)** — The number of minutes it took to complete this workflow, which is calculated as the difference between the `created_at` and `completed_at` values.

service
: *Required* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the [Service](../services.html) that will directly be affected by the workflow implementation, or in case of an emergency workflow, the service that was directly affected by the workflow implementation.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_at
: *Optional* **[datetime](../general/data_types.html)** — The Start at field is used to specify the date and time at which the Status field of the first tasks of the workflow will automatically be set to “Assigned”.

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `registered` — The Status field is automatically set based on the status of the workflow’s tasks. Valid values are:
: - `being_created`: Being Created
 - `registered`: Registered
 - `risk_and_impact`: Risk & Impact — *deprecated: replaced by `in_progress`*
 - `approval`: Approval — *deprecated: replaced replaced by `in_progress`*
 - `implementation`: Implementation — *deprecated: replaced by `in_progress`*
 - `in_progress`: In Progress
 - `progress_halted`: Progress Halted
 - `completed`: Completed

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the objective of the workflow.

template
: *Required* **[reference](../general/data_types.html#references) to [Workflow Template](../workflow_templates.html)** — The Template field contains the link to the workflow template that was used to register the workflow.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the workflow. If the workflow has no updates it contains the `created_at` value.

workflow\_type
: *Required* **[enum](../general/enumerations/index.html)** — The type of the workflow. It contains the value of the Reference field of a [Workflow Type](../workflow_types.html).
