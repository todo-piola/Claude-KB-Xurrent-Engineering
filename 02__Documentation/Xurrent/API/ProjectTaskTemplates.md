# Project Task Templates API

- [List project task templates](../project_task_templates.html#list-project-task-templates)
- [Get a single project task template](../project_task_templates.html#get-a-single-project-task-template)
- [Create a project task template](../project_task_templates.html#create-a-project-task-template)
- [Update a project task template](../project_task_templates.html#update-a-project-task-template)
- [Fields](../project_task_templates.html#fields)

## List project task templates

List all project task templates for an account:

```
GET /project_task_templates
```

### Response

```
status: 200 OK
```

```
[{"id":1034,"sourceID":null,"subject":"Finalize project implementation plan","category":"activity","created_at":"2016-12-23T05:09:04-06:00","updated_at":"2016-12-23T05:09:04-06:00"},{"id":805,"sourceID":null,"subject":"Approval from steering committee","category":"approval","created_at":"2016-12-23T05:09:04-06:00","updated_at":"2016-12-23T05:09:04-06:00"},{"id":371,"sourceID":null,"subject":"Project completed","category":"milestone","created_at":"2016-12-23T05:09:05-06:00","updated_at":"2016-12-23T05:09:05-06:00"},"..."]
```

The response contains [these fields](../project_task_templates.html#collection-fields) by default. [Filtering](../project_task_templates.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of project task templates.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/project_task_templates/disabled`: List all disabled project task templates
- `/project_task_templates/enabled`: List all enabled project task templates

### Collection Fields

By default the following [fields](../project_task_templates.html#fields) will appear in collections of project task templates:

`id` `sourceID` `subject` `impact` `category` `created_at` `updated_at`

Obtain a different set of [fields](../project_task_templates.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../project_task_templates.html#fields):

`id` `source` `sourceID` `subject` `disabled` `category` `created_at` `updated_at`

### Sorting

By default a collection of project task templates is sorted **descending** by `id`.

The following [fields](../project_task_templates.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `category` `created_at` `updated_at` `times_applied`

## Get a single project task template

```
GET /project_task_templates/:id
```

### Response

```
status: 200 OK
```

```
{"assign_to_project_manager":true,"assign_to_requester":false,"assign_to_requester_business_unit_manager":false,"assign_to_requester_manager":false,"assign_to_service_owner":false,"planned_effort_project_manager":240,"planned_effort_requester":null,"planned_effort_requester_business_unit_manager":null,"planned_effort_requester_manager":null,"planned_effort_service_owner":null,"attachments":[],"category":"activity","copy_notes_to_project":false,"created_at":"2016-12-23T05:09:04-06:00","disabled":false,"effort_class":null,"id":1034,"instructions":"Be sure to include a communication plan that will keep everyone informed.","note":null,"planned_duration":1440,"required_approvals":null,"source":null,"sourceID":null,"subject":"Finalize project implementation plan","supplier":null,"times_applied":28,"ui_extension":null,"updated_at":"2016-12-23T05:09:04-06:00"}
```

The response contains [these fields](../project_task_templates.html#fields).

## Create a project task template

```
POST /project_task_templates
```

When creating a new project task template [these fields](../project_task_templates.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"assign_to_project_manager":"...","...":"..."}
```

The response contains [all fields](../project_task_templates.html#fields) of the created project task template and is similar to the response in [Get a single project task template](../project_task_templates.html#get-a-single-project-task-template)

## Update a project task template

```
PATCH /project_task_templates/:id
```

When updating a project task template [these fields](../project_task_templates.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"assign_to_project_manager":"...","...":"..."}
```

The response contains [all fields](../project_task_templates.html#fields) of the updated project task template and is similar to the response in [Get a single project task template](../project_task_templates.html#get-a-single-project-task-template)

## Fields

assign\_to\_project\_manager
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Project manager box is checked if the project manager is to be selected in the Assignees field of a new [project task](../project_tasks.html) when it is being created based on the template.

assign\_to\_requester
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Requester box is checked if a new project task that is being created based on the template is to be assigned to the person who is selected in the Requested for field of the request for which the project was registered.

assign\_to\_requester\_business\_unit\_manager
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Requester’s business unit manager box is checked if a new project task that is being created based on the template is to be assigned to the person who is selected in the Manager field of the business unit to which the organization belongs that is linked to the person who is selected in the Requested for field of the request for which the project was registered.

assign\_to\_requester\_manager
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Requester’s manager box is checked if a new project task that is being created based on the template is to be assigned to the manager of the project’s requester.

assign\_to\_service\_owner
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Service owner box is checked if a new project task that is being created based on the template is to be assigned to the person who is selected in the Service owner field of the service that is linked to the project that the new project task is a part of.

attachments
: *Readonly* **aggregated Attachments**

category
: *Required* **[enum](../general/enumerations/index.html)** — The Category field is used to select the category that needs to be selected in the Category field of a new project task when it is being created based on the template. Valid values are:
: - `activity`: Activity
 - `approval`: Approval
 - `milestone`: Milestone

copy\_notes\_to\_project
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Copy notes to project checkbox is called “Copy notes to project by default” when the project task template is in Edit mode. This box is checked when the Copy note to project box of project tasks that were created based on the template needs to be checked by default.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the project task template was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the project task template may not be used to help register new project tasks.

effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The effort class that is selected by default, when someone registers time on a project task created based on the template.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the project task template.

instructions
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Instructions field is used to enter the information that needs to be copied to the Instructions field of a new project task when it is being created based on the template.

instructions\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Instructions field.

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to enter the information that needs to be copied to the Note field of a new project task when it is being created based on the template.

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Note field.

planned\_duration
: *Required* **[integer](../general/data_types.html) (max 600000)** — The Planned duration field is used to specify the number of minutes that should be entered in the Planned duration field of a new project task when it is being created based on the template.

planned\_effort
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field is used to specify the number of minutes that the team is expected to spend working on a project task that was created based on the template.

planned\_effort\_project\_manager
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field for the project manager is used to specify the number of minutes that the project manager is expected to spend working on a project task that was created based on the template.

planned\_effort\_requester
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field for the requester of the request for which the project was created is used to specify the number of minutes that the requester is expected to spend working on a project task that was created based on the template.

planned\_effort\_requester\_business\_unit\_manager
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field for the business unit manager of the requester of the request for which the project was created is used to specify the number of minutes that the requester’s business unit manager is expected to spend working on a project task that was created based on the template.

planned\_effort\_requester\_manager
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field for the manager of the requester of the request for which the project was created is used to specify the number of minutes that the requester’s manager is expected to spend working on a project task that was created based on the template.

planned\_effort\_service\_owner
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field for the service owner is used to specify the number of minutes that the service owner is expected to spend working on a project task that was created based on the template.

required\_approvals
: *Optional* **[integer](../general/data_types.html)**, default: `1` — The Required approvals field is used to enter the number that needs to be specified in the Required approvals field of a new approval project task when it is being created based on the template.

skill\_pool
: *Optional* **[reference](../general/data_types.html#references) to [Skill Pool](../skill_pools/index.html)** — The skill pool that should be selected in the Skill pool field of a new project task when it is being created based on the template.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

subject
: *Required* **[string](../general/data_types.html) (max 190)** — The Subject field is used to enter a short description that needs to be copied to the Subject field of a new project task when it is being created based on the template.

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the supplier organization that should be selected in the Supplier field of a new project task when it is being created based on the template.

team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Team field is used to select the Team that should be selected in the Team field of a new project task when it is being created based on the template.

times\_applied
: *Readonly* **[integer](../general/data_types.html)** — The number of times the project task template is used to create a project task.

ui\_extension
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field is used to select the UI extension that is to be added to a new project task when it is being created based on the template.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the project task template. If the project task template has no updates it contains the `created_at` value.

work\_hours\_are\_24x7
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — When set to true, the completion target of project tasks created based on the template are calculated using a 24x7 calendar rather than normal business hours.
