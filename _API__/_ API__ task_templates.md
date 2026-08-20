# Task Templates API

- [List task templates](../task_templates.html#list-task-templates)
- [Get a single task template](../task_templates.html#get-a-single-task-template)
- [Create a task template](../task_templates.html#create-a-task-template)
- [Update a task template](../task_templates.html#update-a-task-template)
- [Fields](../task_templates.html#fields)

## List task templates

List all task templates for an account:

```
GET /task_templates
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:13:46-06:00","category":"implementation","sourceID":null,"updated_at":"2016-03-14T03:13:46-06:00","subject":"Inform Operations that events can be ignored","id":40,"impact":"none","disabled":false},{"created_at":"2016-03-14T03:13:46-06:00","category":"approval","sourceID":null,"updated_at":"2016-03-14T03:13:46-06:00","subject":"Windows Server service owner approval","id":39,"impact":null,"disabled":false},"..."]
```

The response contains [these fields](../task_templates.html#collection-fields) by default. [Filtering](../task_templates.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of task templates.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/task_templates/disabled`: List all disabled task templates
- `/task_templates/enabled`: List all enabled task templates

### Collection Fields

By default the following [fields](../task_templates.html#fields) will appear in collections of task templates:

`id` `sourceID` `subject` `impact` `category` `created_at` `updated_at`

Obtain a different set of [fields](../task_templates.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../task_templates.html#fields):

`id` `source` `sourceID` `subject` `impact` `category` `created_at` `updated_at` `disabled`

### Sorting

By default a collection of task templates is sorted **descending** by `id`.

The following [fields](../task_templates.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `impact` `category` `created_at` `updated_at` `times_applied`

## Get a single task template

```
GET /task_templates/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2017-10-21T04:13:52-06:00","category":"implementation","sourceID":null,"updated_at":"22017-11-08T02:49:28-06:00","supplier":null,"member":null,"subject":"Move desktop PC","id":329,"times_applied":3,"planned_duration":960,"planned_effort":120,"required_approvals":null,"instructions":"Pick up the desktop PC and take it to its new location.","note":null,"attachments":[],"pdf_design":null,"effort_class":null,"copy_notes_to_workflow":false,"assign_to_workflow_manager":false,"assign_to_service_owner":false,"assign_to_requester":false,"assign_to_requester_manager":false,"assign_to_requester_business_unit_manager":false,"planned_effort_workflow_manager":null,"planned_effort_requester":null,"planned_effort_requester_business_unit_manager":null,"planned_effort_requester_manager":null,"planned_effort_service_owner":null,"impact":null,"disabled":false,"team":{"id":10,"name":"End-User Support, Houston"},"source":null,"ui_extension":null,"urgent":false}
```

The response contains [these fields](../task_templates.html#fields).

## Create a task template

```
POST /task_templates
```

When creating a new task template [these fields](../task_templates.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"assign_to_workflow_manager":"...","...":"..."}
```

The response contains [all fields](../task_templates.html#fields) of the created task template and is similar to the response in [Get a single task template](../task_templates.html#get-a-single-task-template)

## Update a task template

```
PATCH /task_templates/:id
```

When updating a task template [these fields](../task_templates.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"assign_to_workflow_manager":"...","...":"..."}
```

The response contains [all fields](../task_templates.html#fields) of the updated task template and is similar to the response in [Get a single task template](../task_templates.html#get-a-single-task-template)

## Fields

assign\_to\_workflow\_manager
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Workflow manager box is checked if a new task that is being created based on the template is to be assigned to the person who is selected in the Manager field of the workflow to which the task belongs.

assign\_to\_requester
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Requester box is checked if a new task that is being created based on the template is to be assigned to the person who is selected in the Requested for field of the request for which the workflow is being generated.

assign\_to\_requester\_business\_unit\_manager
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Requester’s business unit manager box is checked if a new task that is being created based on the template is to be assigned to the person who is selected in the Manager field of the business unit to which the organization belongs that is linked to the person who is selected in the Requested for field of the request for which the workflow is being generated.

assign\_to\_requester\_manager
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Requester’s manager box is checked if the manager of the requester of the first related request is to be selected in the Approver field of a new task when it is being created based on the template.

assign\_to\_service\_owner
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Service owner box is checked if a new task that is being created based on the template is to be assigned to the person who is selected in the Service owner field of the service that is linked to the workflow that the new task is a part of.

attachments
: *Readonly* **aggregated Attachments**

category
: *Required* **[enum](../general/enumerations/index.html)** — The Category field is used to select the category that needs to be selected in the Category field of a new task when it is being created based on the template. Valid values are:
: - `risk_and_impact`: Risk & Impact
 - `approval`: Approval
 - `implementation`: Implementation
 - `fulfillment_placeholder`: Fulfillment Placeholder
 - `automation`: Automation

copy\_notes\_to\_request
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Copy notes to request checkbox is called “Copy notes to request by default” when the task template is in Edit mode. This box is checked when the Copy note to request box of tasks that were created based on the template needs to be checked by default.

copy\_notes\_to\_workflow
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Copy notes to workflow checkbox is called “Copy notes to workflow by default” when the task template is in Edit mode. This box is checked when the Copy note to workflow box of tasks that were created based on the template needs to be checked by default.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the task template was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the task template may not be used to help register new tasks.

effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The effort class that is selected by default, when someone registers time on a task created based on the template.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the task template.

impact
: *Optional* **[enum](../general/enumerations/index.html)** — The Impact field is used to select the impact level that needs to be selected in the Impact field of a new task when it is being created based on the template. Valid values are:
: - `none`: None - Service Not Degraded
 - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

instructions
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Instructions field is used to enter the information that needs to be copied to the Instructions field of a new task when it is being created based on the template.

instructions\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Instructions field.

member
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Member field is used to select the [Person](../people.html) who should be selected in the Member field of a new task when it is being created based on the template.

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to enter the information that needs to be copied to the Note field of a new task when it is being created based on the template.

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Note field.

planned\_duration
: *Required* **[integer](../general/data_types.html) (max 600000)** — The Planned duration field is used to specify the number of minutes that should be entered in the Planned duration field of a new task when it is being created based on the template.

planned\_effort
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field is used to specify the number of minutes the member is expected to spend working on a task that was created based on the template.

planned\_effort\_workflow\_manager
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort for workflow manager field is used to specify the number of minutes the workflow manager is expected to spend working on a task that was created based on the template.

planned\_effort\_requester
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort for requester field is used to specify the number of minutes the person, who is selected in the Requested for field of the first related request, is expected to spend working on a task that was created based on the template.

planned\_effort\_requester\_business\_unit\_manager
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort for business unit manager of requester field is used to specify the number of minutes the business unit manager of the requester of the first related request is expected to spend working on a task that was created based on the template.

planned\_effort\_requester\_manager
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort for manager of requester field is used to specify the number of minutes the manager of the requester of the first related request is expected to spend working on a task that was created based on the template.

planned\_effort\_service\_owner
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort for service owner field is used to specify the number of minutes the owner of the service of the related to the workflow is expected to spend working on a task that was created based on the template.

provider\_not\_accountable
: *Optional* **[boolean](../general/data_types.html)** — The Provider not accountable field value is used to indicate whether the provider is not to be accountable for the affected SLAs linked to the requests that are linked to the workflow of a task that was created based on the template, as long as the task is active.

request\_template
: *Optional* **[reference](../general/data_types.html#references) to [Request Template](../request_templates.html)** — The Request template field is used to select the [Request template](../request_templates.html) that must be used to generate a new request when a task based on the task template is started.

request\_service\_instance
: *Optional* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The Service instance field is used to select the [Service instance](../service_instances/index.html) that must be applied to the new request that is generated when a task based on the task template is started.

required\_approvals
: *Optional* **[integer](../general/data_types.html)**, default: `1` — The Required approvals field is used to enter the number that needs to be specified in the Required approvals field of a new approval task when it is being created based on the template.

skill\_pool
: *Optional* **[reference](../general/data_types.html#references) to [Skill Pool](../skill_pools/index.html)** — The skill pool that should be selected in the Skill pool field of a new task when it is being created based on the template.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

subject
: *Required* **[string](../general/data_types.html) (max 190)** — The Subject field is used to enter a short description that needs to be copied to the Subject field of a new [Task](../tasks.html) when it is being created based on the template.

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the supplier [Organization](../organizations.html) that should be selected in the Supplier field of a new task when it is being created based on the template.

team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Team field is used to select the [Team](../teams.html) that should be selected in the Team field of a new task when it is being created based on the template.

times\_applied
: *Readonly* **[integer](../general/data_types.html)** — The number of times the task template is used to create a Task.

ui\_extension
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field is used to select the UI extension that is to be added to a new task when it is being created based on the template.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the task template. If the task template has no updates it contains the `created_at` value.

urgent
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Mark as urgent box is checked when a new task that is created based on the template is to be marked as urgent.

work\_hours\_are\_24x7
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — When set to true, the completion target of tasks created based on the template are calculated using a 24x7 calendar rather than normal business hours.
