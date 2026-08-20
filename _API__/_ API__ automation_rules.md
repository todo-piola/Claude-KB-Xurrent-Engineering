# Automation Rules API

- [List automation rules](../automation_rules.html#list-automation-rules)
- [Get a single automation rule](../automation_rules.html#get-a-single-automation-rule)
- [Create an automation rule](../automation_rules.html#create-an-automation-rule)
- [Update an automation rule](../automation_rules.html#update-an-automation-rule)
- [Delete an automation rule](../automation_rules.html#delete-an-automation-rule)
- [Fields](../automation_rules.html#fields)

## List automation rules

List all automation rules for an account:

```
GET /automation_rules
```

### Response

```
status: 200 OK
```

```
[{"id":21,"disabled":false,"name":"Cancel task for new telephone","trigger":"on status update","position":2,"created_at":"2020-02-15T05:08:46-06:00","updated_at":"2020-02-15T05:08:46-06:00"},{"id":20,"disabled":false,"name":"Add email address to AD task","trigger":"on status update","position":1,"created_at":"2020-02-15T05:08:46-06:00","updated_at":"2020-02-15T05:08:46-06:00"}]
```

The response contains [these fields](../automation_rules.html#collection-fields) by default. [Filtering](../automation_rules.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of automation rules.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/automation_rules/for_requests`: List all automation rules for requests
- `/automation_rules/for_request_templates`: List all automation rules for request templates
- `/automation_rules/for_problems`: List all automation rules for problems
- `/automation_rules/for_tasks`: List all automation rules for tasks
- `/automation_rules/for_task_templates`: List all automation rules for task templates
- `/automation_rules/for_workflows`: List all automation rules for workflows
- `/automation_rules/for_workflow_templates`: List all automation rules for workflow templates
- `/automation_rules/for_project_tasks`: List all automation rules for project tasks
- `/automation_rules/for_project_task_templates`: List all automation rules for project task templates
- `/automation_rules/for_project_templates`: List all automation rules for project templates
- `/automation_rules/for_cis`: List all automation rules for configuration items
- `/automation_rules/for_risks`: List all automation rules of risks
- `/automation_rules/for_scim_users`: List all automation rules for SCIM users
- `/automation_rules/for_scim_groups`: List all automation rules for SCIM groups
- `/automation_rules/disabled`: List all disabled automation rules
- `/automation_rules/enabled`: List all enabled automation rules

### Collection Fields

By default the following fields will appear in collections of automation rules:

`id` `disabled` `name` `trigger` `position` `created_at` `updated_at`

In addition, one or two of the following fields appears, depending on the type of the automation rule:

`generic` `request` `request_template` `task` `task_template` `workflow` `workflow_template` `project_task` `project_task_template` `project_template`

Obtain a different set of [fields](../automation_rules.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../automation_rules.html#fields):

`id` `sourceID`

The filter on `sourceID` is not case sensitive.

### Sorting

By default a collection of automation rules is sorted **descending** by `id`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `position`

## Get a single automation rule

```
GET /automation_rules/:id
```

### Response

```
status: 200 OK
```

```
{"actions":"a1: update badge_task add note 'This task was canceled because a security badge was not requested for the new employee.'\na2: update badge_task set status = canceled","actions_html":"a1: update badge_task add note '<p>This task was canceled because a security badge was not requested for the new employee.</p>'\na2: update badge_task set status = canceled","condition":"is_assigned and !badge","created_at":"2020-02-15T05:08:46-06:00","description":"This rule cancels the task for preparing a security badge for the new employee if this was not requested.","description_html":"<p>This rule cancels the task for preparing a security badge for the new employee if this was not requested.</p>","disabled":false,"expressions":"is_assigned: status = assigned\nrequest: workflow.requests[first]\nbadge: request.custom_fields.badge\nbadge_task: workflow.tasks['Prepare a security badge']","generic":false,"id":22,"name":"Cancel task for new badge","position":3,"source":null,"sourceID":null,"trigger":"on status update","updated_at":"2020-02-15T05:08:46-06:00","workflow_template":{"id":22,"subject":"Prepare services for new employee"},"task_template":{"id":69,"subject":"Cancel tasks that do not need to be completed"}}
```

The response contains [these fields](../automation_rules.html#fields).

## Create an automation rule

```
POST /automation_rules
```

When creating a new automation rule [these fields](../automation_rules.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"amount":"...","...":"..."}
```

The response contains [all fields](../automation_rules.html#fields) of the created automation rule and is similar to the response in [Get a single automation rule](../automation_rules.html#get-a-single-automation-rule).

## Update an automation rule

```
PATCH /automation_rules/:id
```

When updating an automation rule [these fields](../automation_rules.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"amount":"...","...":"..."}
```

The response contains [all fields](../automation_rules.html#fields) of the updated automation rule and is similar to the response in [Get a single automation rule](../automation_rules.html#get-a-single-automation-rule).

## Delete an automation rule

```
DELETE /automation_rules/:id
```

### Response

```
status: 204 No Content
```

The response contains no body.

## Fields

actions
: *Optional* **[string](../general/data_types.html) (max 64KB)** — The Actions field is used to define actions that should be executed when the condition of the automation rule is met. For example:

```
a1: update badge_task add note 'This task was canceled by automation.'
a2: update badge_task set status = canceled
```

actions\_html
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — Contents of the Actions field converted to HTML.

condition
: *Optional* **[string](../general/data_types.html) (max 64KB)** — The Condition field is used to define the condition that needs to be met in order for the update action(s) of the rule to be performed. For example: `is_assigned and !badge`.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the automation rule was created.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to enter a high-level description of the automation rule’s function. The available formatting options are described in the [Text Formatting](../general/text_formatting.html) section.

description\_html
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — Contents of the Description field converted to HTML.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the automation rule should not be triggered.

expressions
: *Optional* **[string](../general/data_types.html) (max 64KB)** — The Expressions field is used to define expressions that can subsequently be used to define the rule’s conditions and the update action(s) that the rule is to perform. For example:

```
is_assigned: status = assigned
request: workflow.requests[first]
badge: request.custom_fields.badge
badge_task: workflow.tasks['Prepare a security badge']
```

generic
: *Optional* **[string](../general/data_types.html) (max 128)** — When the automation rule is not linked to one specific record but to all records of a type, the Generic field contains the record type. Valid values are:
: - `request`
: - `problem`
 - `workflow`
 - `task`
 - `risk`
 - `ci`
 - `scim_user`
 - `scim_group`

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the automation rule.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the automation rule.

position
: *Optional* **[integer](../general/data_types.html)** — The Position field dictates the order in which the automation rule is executed.

project\_task
: *Optional* **[reference](../general/data_types.html#references) to [Project Task](../project_tasks.html)** — The project task that the automation rule is linked to.

project\_task\_template
: *Optional* **[reference](../general/data_types.html#references) to [Project Task Template](../project_task_templates.html)** — The project task template that the automation rule is linked to.

project\_template
: *Optional* **[reference](../general/data_types.html#references) to [Project Template](../project_templates/index.html)** — The project template that the automation rule is linked to.

request
: *Optional* **[reference](../general/data_types.html#references) to [Request](../requests.html)** — The request that the automation rule is linked to.

request\_template
: *Optional* **[reference](../general/data_types.html#references) to [Request Template](../request_templates.html)** — The request template that the automation rule is linked to.

source
: *Optional* **[string](../general/data_types.html) (max 30)** — See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** — See [source](../general/source.html)

task
: *Optional* **[reference](../general/data_types.html#references) to [Task](../tasks.html)** — The Task that the automation rule is linked to.

task\_template
: *Optional* **[reference](../general/data_types.html#references) to [Task Template](../task_templates.html)** — The Task Template that the automation rule is linked to.

trigger
: *Required* **[string](../general/data_types.html) (max 128)** — The Trigger field is used to specify when the automation rule is to be triggered, for example `on status update` or `on note added`.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the automation rule. If the automation rule has no updates it contains the `created_at` value.

workflow
: *Optional* **[reference](../general/data_types.html#references) to [Workflow](../workflows.html)** — The workflow that the automation rule is linked to.

workflow\_template
: *Optional* **[reference](../general/data_types.html#references) to [Workflow Template](../workflow_templates.html)** — The workflow template that the automation rule is linked to.
