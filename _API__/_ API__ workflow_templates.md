# Workflow Templates API

- [List workflow templates](../workflow_templates.html#list-workflow-templates)
- [Get a single workflow template](../workflow_templates.html#get-a-single-workflow-template)
- [Create a workflow template](../workflow_templates.html#create-a-workflow-template)
- [Update a workflow template](../workflow_templates.html#update-a-workflow-template)
- [Fields](../workflow_templates.html#fields)

## List workflow templates

List all workflow templates for an account:

```
GET /workflow_templates
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:13:47-06:00","sourceID":null,"updated_at":"2016-03-14T03:13:47-06:00","service":{"name":"Windows Server","id":33,"provider":{"name":"Widget Data Center, External IT","id":30}},"subject":"Windows server hardware upgrade","id":9,"disabled":false},{"created_at":"2016-03-14T03:13:47-06:00","sourceID":null,"updated_at":"2016-03-14T03:13:47-06:00","service":{"name":"Personal Computing","id":22,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"subject":"Move desktop personal computer","id":8,"disabled":false,"recurrence":{"start_date":"2016-03-16","day_of_week":true,"day_of_week_index":"first","next_occurrence_at":"2016-04-02T02:00:00-05:00","day_of_week_day":"monday","last_occurrence_at":null,"day":null,"time_of_day":"09:00","day_of_month":null,"interval":1,"ical":"DTSTART;TZID=CET:20160316T000000\nRRULE:FREQ=YEARLY;BYMONTH=1,4,7,10;BYDAY=1MO","disabled":false,"frequency":"yearly","last_occurrence_object":null,"month_of_year":"1,4,7,10","time_zone":"Amsterdam","end_date":null,"last_occurrence_errors":null}},"..."]
```

The response contains [these fields](../workflow_templates.html#collection-fields) by default. [Filtering](../workflow_templates.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of workflow templates.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/workflow_templates/disabled`: List all disabled workflow templates
- `/workflow_templates/enabled`: List all enabled workflow templates

### Collection Fields

By default the following [fields](../workflow_templates.html#fields) will appear in collections of workflow templates:

`id` `sourceID` `subject` `service` `created_at` `updated_at`

Obtain a different set of [fields](../workflow_templates.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../workflow_templates.html#fields):

`id` `source` `sourceID` `subject` `disabled` `service` `created_at` `updated_at`

### Sorting

By default a collection of workflow templates is sorted **descending** by `id`.

The following [fields](../workflow_templates.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `service` `created_at` `updated_at` `times_applied`

## Get a single workflow template

```
GET /workflow_templates/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2016-03-14T03:13:47-06:00","category":"non_standard","sourceID":null,"workflow_manager_id":null,"recurrence":null,"updated_at":"2016-03-14T03:13:47-06:00","service":null,"subject":"Empty workflow template","id":1,"times_applied":0,"note":null,"justification":null,"impact":"none","disabled":false,"source":null,"instructions":"Add tasks to this workflow to ensure risk and impact analysis is performed, approvals are collected and all implementation steps defined.","workflow_type":null,"ui_extension":null}
```

The response contains [these fields](../workflow_templates.html#fields).

## Create a workflow template

```
POST /workflow_templates
```

When creating a new workflow template [these fields](../workflow_templates.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](../workflow_templates.html#fields) of the created workflow template and is similar to the response in [Get a single workflow template](../workflow_templates.html#get-a-single-workflow-template)

## Update a workflow template

```
PATCH /workflow_templates/:id
```

When updating a workflow template [these fields](../workflow_templates.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](../workflow_templates.html#fields) of the updated workflow template and is similar to the response in [Get a single workflow template](../workflow_templates.html#get-a-single-workflow-template)

## Fields

assign\_relations\_to\_workflow\_manager
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — Whether relations like Requests and Problems are assigned to the workflow manager when the relations are linked to the workflow.

attachments
: *Readonly* **aggregated Attachments**

category
: *Optional* **[enum](../general/enumerations/index.html)** — The Category field is used to select the category that needs to be selected in the Category field of a new workflow when it is being created based on the template. Valid values are:
: - `standard`: Standard - Approved Workflow Template Was Used
 - `non_standard`: Non-Standard - Approved Workflow Template Not Available
 - `emergency`: Emergency - Required for Incident Resolution
 - `order`: Order - Organization Order Workflow

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the workflow template was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the workflow template may not be used to help register new workflows.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the workflow template.

impact
: *Readonly* **[enum](../general/enumerations/index.html)**, default: `none` — The Impact field shows the maximum impact level that is selected in the task templates that are a part of the workflow template. Valid values are:
: - `none`: None - Service Not Degraded
 - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

instructions
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Instructions field is used to enter the information that needs to be shown when a new workflow is being created based on the template. This field typically contains instructions about how to register the workflow.

instructions\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Instructions field.

justification
: *Optional* **[enum](../general/enumerations/index.html)** — The Justification field is used to select the justification that needs to be selected in the Justification field of a new workflow when it is being created based on the template. This field is required when there are request templates linked to the workflow template. Valid values are:
: - `compliance`: Compliance
 - `correction`: Correction
 - `expansion`: Expansion
 - `improvement`: Improvement
 - `maintenance`: Maintenance
 - `move`: Move
 - `removal`: Removal
 - `replacement`: Replacement
 - `purchase`: Purchase

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to enter the information that needs to be copied to the Note field of a new workflow when it is being created based on the template.

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Note field.

prevent\_request\_completion
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether permissions to complete linked requests are restricted.

recurrence
: *Optional* **aggregated** — The recurrence settings hash, missing in case the workflow template has no recurrency defined. See [Recurrence](../recurrences.html) for the fields in the recurrence hash.

service
: *Optional* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the [Service](../services.html) that should be selected in the Service field of a new workflow when it is being created based on the template.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description that needs to be copied to the Subject field of a new [Workflow](../workflows.html) when it is being created based on the template.

times\_applied
: *Readonly* **[integer](../general/data_types.html)** — The number of times the workflow template is used to create a Workflow.

ui\_extension
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field is used to select the UI extension that is to be added to a new workflow when it is being created based on the template.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the workflow template. If the workflow template has no updates it contains the `created_at` value.

workflow\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Workflow manager field is used to select the [Person](../people.html) who will be responsible for coordinating the workflows that will be generated automatically in accordance with the recurrence schedule.

workflow\_type
: *Optional* **[enum](../general/enumerations/index.html)** — The Type field is used to select the type of a new workflow when it is being created based on the template. It contains the value of the Reference field of a [Workflow Type](../workflow_types.html).
