# Projects API

- [List projects](index.html#list-projects)
- [Get a single project](index.html#get-a-single-project)
- [Create a project](index.html#create-a-project)
- [Update a project](index.html#update-a-project)
- [Archive a project](index.html#archive-a-project)
- [Trash a project](index.html#trash-a-project)
- [Restore a project](index.html#restore-a-project)
- [Fields](index.html#fields)

## List projects

List all projects for an account:

```
GET /projects
```

### Response

```
status: 200 OK
```

```
[{"id":7345,"sourceID":null,"subject":"Warehouse Ordering (WHO)","category":"large","status":"in_progress","completion_target_at":"2017-01-13T09:00:00-06:00","completed_at":null,"service":{"id":41,"name":"Warehouse Management","provider":{"id":44,"name":"Widget Data Center, External IT","account":{"id":"widget","name":"Widget International"}},"localized_name":"Warehouse Management"},"created_at":"2016-11-13T13:17:00-06:00","updated_at":"2016-12-23T05:09:09-06:00"},{"id":4021,"sourceID":null,"subject":"Best in Customer Satisfaction (BICS)","category":"medium","status":"in_progress","completion_target_at":"2017-03-21T10:51:00-05:00","completed_at":null,"service":{"id":24,"name":"Service Management (ITRP)","provider":{"id":44,"name":"Widget Data Center, External IT","account":{"id":"widget","name":"Widget International"}},"localized_name":"Service Management (ITRP)"},"created_at":"2016-08-05T16:12:00-05:00","updated_at":"2017-01-18T16:15:34-06:00"}]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of projects.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/projects/completed`: List all completed projects
- `/projects/open`: List all open projects
- `/projects/managed_by_me`: List all projects which manager is the API user

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of projects:

`id` `sourceID` `subject` `manager` `category` `status` `completion_target_at` `completed_at` `service` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `subject` `category` `status` `completion_target_at` `completed_at` `service` `created_at` `updated_at`

### Sorting

By default a collection of projects is sorted **descending** by `id`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `category` `status` `completion_target_at` `completed_at` `service` `created_at` `updated_at`

### Response

The response is similar to the response in [List projects](index.html#list-projects)

## Get a single project

```
GET /projects/:id
```

### Response

```
status: 200 OK
```

```
{"category":"large","completed_at":null,"completion_reason":null,"completion_target_at":"2017-01-13T09:00:00-06:00","created_at":"2016-11-13T13:17:00-06:00","custom_fields":null,"customer":{"id":52,"name":"Widget North America, Manufacturing","account":{"id":"widget","name":"Widget International"}},"id":7345,"cost_of_effort":"320000.0","cost_of_purchases":"2315000.0","effort":3200,"risk_level":"significant","roi":6,"total_cost":"2635000.0","value":"2800000.0","justification":"improvement","manager":{"id":156,"name":"Ellen Brown","account":{"id":"widget","name":"Widget International"}},"program":"Manufacturing Improvements","service":{"id":41,"name":"Warehouse Management","provider":{"id":44,"name":"Widget Data Center, External IT","account":{"id":"widget","name":"Widget International"}},"localized_name":"Warehouse Management"},"source":"4me","sourceID":null,"status":"in_progress","subject":"Warehouse Ordering (WHO)","time_zone":"Central Time (US & Canada)","ui_extension":null,"updated_at":"2016-12-23T05:09:09-06:00","work_hours":{"id":42,"name":"Monday through Friday, 9:00am until 5:00pm"}}
```

The response contains [these fields](index.html#fields).

## Create a project

```
POST /projects
```

When creating a new project [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created project and is similar to the response in [Get a single project](index.html#get-a-single-project)

## Update a project

```
PATCH /projects/:id
```

When updating a project [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated project and is similar to the response in [Get a single project](index.html#get-a-single-project)

## Archive a project

```
POST /projects/:id/archive
```

Moves a given project to the [Archive](../archive/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the project.

### Response

```
status: 200 OK
```

```
{"archived":"true","category":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the archived project and is similar to the response in [Get a single project](index.html#get-a-single-project)

## Trash a project

```
POST /projects/:id/trash
```

Moves a given project to the [Trash](../trash/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the project.

### Response

```
status: 200 OK
```

```
{"trashed":"true","category":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the archived project and is similar to the response in [Get a single project](index.html#get-a-single-project)

## Restore a project

```
POST /projects/:id/restore
```

Moves a given project from the [Archive](../archive/index.html) or the [Trash](../trash/index.html) back into the view of “Completed Projects”.
This action requires the Account Administrator or Directory Administrator role in the account of the project.

### Response

```
status: 200 OK
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the archived project and is similar to the response in [Get a single project](index.html#get-a-single-project)

## Fields

attachments
: *Readonly* **aggregated Attachments**
: Use [Projects - Notes API](notes/index.html) to get note attachments.

category
: *Optional* **[enum](../general/enumerations/index.html)** with `reference` field of [Project Category](../project_categories/index.html) — The Category field is used to select the category of the project.

completed\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Completed at field is automatically set to the date and time at which the project is saved with the status “Completed”.

completion\_reason
: *Optional* **[enum](../general/enumerations/index.html)** — The Completion reason field is used to select the appropriate completion reason for the project when it has been completed. It is automatically set to “Complete” when all tasks related to the project have reached the status “Completed”, “Approved” or “Canceled”. Valid values are:
: - `withdrawn`: Withdrawn - Withdrawn by Requester
 - `rejected`: Rejected - Rejected by Approver
 - `abandoned`: Abandoned - Not Implemented
 - `partial`: Partial - Not Entirely Implemented
 - `complete`: Complete - Fully Implemented

completion\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Completion target field shows the target date and time of the last task of the project.

cost\_of\_effort
: *Optional* **[decimal](../general/data_types.html)** — The Cost of effort field is used to specify the estimated cost of the effort that will be needed from internal employees and/or long-term contractors to implement the project.

cost\_of\_purchases
: *Optional* **[decimal](../general/data_types.html)** — The Cost of purchases field is used to specify the estimated cost of all purchases (for equipment, consulting effort, licenses, etc.) needed to implement the project. Recurring costs that will be incurred following the implementation of the project are to be included for the entire ROI calculation period.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the project was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the project.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

customer
: *Required* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Customer field is used to select the organization for which the project is to be implemented.

effort
: *Optional* **[integer](../general/data_types.html)** — The Effort field is used to specify the estimated number of hours of effort that will be needed from internal employees and/or long-term contractors to implement the project.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the project.

justification
: *Required* **[enum](../general/enumerations/index.html)** — The Justification field is used to select the reason why the project should be considered for implementation. Valid values are:
: - `compliance`: Compliance
 - `correction`: Correction
 - `expansion`: Expansion
 - `improvement`: Improvement
 - `maintenance`: Maintenance
 - `move`: Move
 - `removal`: Removal
 - `replacement`: Replacement

manager
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field is used to select the person who is responsible for coordinating the implementation of the project.

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to provide a high-level description of the project. It is also used to add any information that could prove useful for anyone involved in the project, including the people whose approval is needed and the people who are helping to implement it.
: The Note field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Note field.

program
: *Required* **[string](../general/data_types.html) (max 80)** — The Program field is used to indicate which program the project is a part of. A previously entered program name can be selected, or a new one can be entered.

resolution\_duration
: *Readonly* **[integer](../general/data_types.html)** — The number of minutes it took to complete this project, which is calculated as the difference between the `created_at` and `completed_at` values.

risk\_level
: *Optional* **[enum](../general/enumerations/index.html)** with `reference` field of [Project Risk Level](../project_risk_levels/index.html) — The Risk level field is used to select the risk level of the project.

roi
: *Readonly* **[integer](../general/data_types.html)** — The ROI field displays the estimated return on investment for the project. This percentage is calculated by dividing the value, minus the total costs, by the total costs and multiplying the result by 100.

service
: *Required* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the service for which the project will be implemented.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `registered` — The Status field is automatically set based on the status of the project’s tasks. Valid values are:
: - `registered`: Registered
 - `in_progress`: In Progress
 - `progress_halted`: Progress Halted
 - `completed`: Completed

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the objective of the project.

time\_zone
: *Required* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the selected work hours.

total\_cost
: *Readonly* **[decimal](../general/data_types.html)** — The Total costs field displays the total estimated cost to implement the project. This is the sum of the estimated cost of effort and cost of purchases.

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the project.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the project. If the project has no updates it contains the `created_at` value.

value
: *Optional* **[decimal](../general/data_types.html)** — The Value field is used to specify the estimated financial value that the implementation of the project will deliver for the entire ROI calculation period.

value\_currency
: *Optional* **[enum](../general/enumerations/index.html)** — The currency of the Value field value of the project. For valid values, see the list of currencies in the Currency field of the [Account API](../account.html).

work\_hours
: *Required* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Work hours field is used to select a calendar that defines the work hours that are to be used to calculate the anticipated assignment and completion target for the tasks of the project.
