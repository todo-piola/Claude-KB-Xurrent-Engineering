# App Offering Automation Rules API

- [List app offering automation rules](index.html#list-app-offering-automation-rules)
- [Get a single app offering automation rule](index.html#get-a-single-app-offering-automation-rule)
- [Create an app offering automation rule](index.html#create-an-app-offering-automation-rule)
- [Update an app offering automation rule](index.html#update-an-app-offering-automation-rule)
- [Delete an app offering automation rule](index.html#delete-an-app-offering-automation-rule)
- [Fields](index.html#fields)

## List App Offering Automation Rules

List all app offering automation rules for an account:

```
GET /app_offering_automation_rules
```

### Response

```
status: 200 OK
```

```
[{"id":1,"app_offering":{"reference":"note-dispatcher","id":1},"rulable_type":"Req","name":"Trigger webhook for each note added","trigger":"on note added","position":1,"created_at":"2021-04-13T04:19:50-05:00","updated_at":"2021-04-13T04:19:50-05:00","...":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of app offering automation rules.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/app_offering_automation_rules/for_requests`: List all app offering automation rules for requests
- `/app_offering_automation_rules/for_tasks`: List all app offering automation rules for tasks
- `/app_offering_automation_rules/for_cis`: List all app offering automation rules for configuration items
- `/app_offering_automation_rules/for_problems`: List all app offering automation rules for problems

### Collection Fields

By default the following fields will appear in collections of app offering automation rules:

`id` `app_offering` `rulable_type` `name` `trigger` `position` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `app_offering` `created_at` `updated_at`

### Sorting

By default a collection of app offering automation rules is not sorted.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `position`

## Get a single app offering automation rule

```
GET /app_offering_automation_rules/:id
```

### Response

```
status: 200 OK
```

```
{"id":1,"app_offering":{"reference":"note-dispatcher","id":1},"rulable_type":"Req","name":"Trigger webhook for each note added","trigger":"on note added","position":1,"created_at":"2021-04-13T04:19:50-05:00","updated_at":"2021-04-13T04:19:50-05:00","...":"..."}
```

The response contains [these fields](index.html#fields).

## Create an app offering automation rule

```
POST /app_offering_automation_rules
```

When creating a new app offering automation rule [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created app offering automation rule and is similar to the response in [Get a single app offering automation rule](index.html#get-a-single-app-offering-automation-rule).

## Update an app offering automation rule

```
PATCH /app_offering_automation_rules/:id
```

When updating a app offering automation rule [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated app offering automation rule and is similar to the response in [Get a single app offering automation rule](index.html#get-a-single-app-offering-automation-rule).

## Delete an app offering automation rule

```
DELETE /app_offering_automation_rules/:id
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

expressions
: *Optional* **[string](../general/data_types.html) (max 64KB)** — The Expressions field is used to define expressions that can subsequently be used to define the rule’s conditions and the update action(s) that the rule is to perform. For example:

```
is_assigned: status = assigned
request: workflow.requests[first]
badge: request.custom_fields.badge
badge_task: workflow.tasks['Prepare a security badge']
```

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the automation rule.

app\_offering
: *Required* **[reference](../general/data_types.html#references) to [App Offering](../app_offerings/index.html)** — This field references the App Offering this automation rule belongs to.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the automation rule.

position
: *Optional* **[integer](../general/data_types.html)** — The Position field dictates the order in which the automation rule is executed.

rulable\_type
: *Required* **[string](../general/data_types.html) (max 128)** — The Generic field contains the record type. Valid values are:
: - `Req`
 - `Task`
 - `Ci`
 - `Problem`

trigger
: *Required* **[string](../general/data_types.html) (max 128)** — The Trigger field is used to specify when the automation rule is to be triggered, for example `on status update` or `on note added`.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the automation rule. If the automation rule has no updates it contains the `created_at` value.
