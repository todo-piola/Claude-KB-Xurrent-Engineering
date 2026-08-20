# Time Entries API

- [List time entries](../time_entries.html#list-time-entries)
- [Get a single time entry](../time_entries.html#get-a-single-time-entry)
- [Create a time entry](../time_entries.html#create-a-time-entry)
- [Update a time entry](../time_entries.html#update-a-time-entry)
- [Remove a time entry](../time_entries.html#remove-a-time-entry)
- [Archive a time entry](../time_entries.html#archive-a-time-entry)
- [Trash a time entry](../time_entries.html#trash-a-time-entry)
- [Restore a time entry](../time_entries.html#restore-a-time-entry)
- [Fields](../time_entries.html#fields)

## List time entries

List all time entries for an account:

```
GET /time_entries
```

### Response

```
status: 200 OK
```

```
[{"id":195,"date":"2016-03-28","correction":false,"created_at":"2016-03-28T12:13:11-05:00","updated_at":"2016-03-28T12:13:11-05:00","time_spent":120,"organization":{"id":7,"name":"Widget North America, Information Technology"},"person":{"id":7,"name":"Chess Cole"},"time_allocation":{"id":4,"group":"Project","name":"Transparency of Performance (TOP)","account":{"id":"wna-it","name":"Widget N. America - IT"},"localized_group":"Project","localized_name":"Transparency of Performance (TOP)"},"service":{"id":36,"name":"SAP Basis","localized_name":"SAP Basis"},"customer":{"id":8,"name":"Widget North America, Human Resources"},"description":"Transaction response time testing for new HR features."},{"id":231,"date":"2016-03-28","created_at":"2016-03-28T14:55:00-05:00","updated_at":"2016-03-28T14:57:00-05:00","time_spent":10,"organization":{"id":44,"name":"Widget Data Center, External IT"},"person":{"id":57,"name":"Tom Waters"},"request":{"id":70248,"subject":"Expense reporting is slow","account":{"id":"wna-it","name":"Widget N. America - IT"},"service":{"id":22,"name":"Expense Reporting","localized_name":"Expense Reporting"},"customer":{"id":48,"name":"Widget North America, Sales & Marketing"}}},"..."]
```

The response contains [these fields](../time_entries.html#collection-fields) by default. [Filtering](../time_entries.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of time entries.

### Collection Fields

By default the following [fields](../time_entries.html#fields) will appear in collections of time entries:

`id` `date` `time_spent` `person` `request` (only when available) `problem` (only when available) `task` (only when available) `project_task` (only when available) `time_allocation` (only when available) `service` `customer` `organization` `description` `deleted` `created_at` `updated_at`

Obtain a different set of [fields](../time_entries.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

Note that the `problem`, `request`, `task` and `project_task` fields
cannot be specified using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).
These fields will appear when the `time_allocation` field is specified.

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../time_entries.html#fields):

`id` `source` `sourceID` `date` `created_at` `updated_at` `deleted` `person`

### Sorting

By default a collection of time entries is sorted **ascending** by `id`.

The following [fields](../time_entries.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `date` `created_at` `updated_at`

## Get a single time entry

```
GET /time_entries/:id
```

### Response

```
status: 200 OK
```

```
{"id":195,"date":"2016-03-28","deleted":false,"correction":false,"created_at":"2016-03-28T12:13:11-05:00","updated_at":"2016-03-28T12:13:11-05:00","time_spent":120,"organization":{"id":7,"name":"Widget North America, Information Technology"},"person":{"id":7,"name":"Chess Cole"},"time_allocation":{"id":4,"group":"Project","name":"Transparency of Performance (TOP)","account":{"id":"wna-it","name":"Widget N. America - IT"},"localized_group":"Project","localized_name":"Transparency of Performance (TOP)"},"service":{"id":36,"name":"SAP Basis","localized_name":"SAP Basis"},"customer":{"id":8,"name":"Widget North America, Human Resources"},"description":"Transaction response time testing for new HR features."}
```

The response contains [these fields](../time_entries.html#fields).

## Create a time entry

```
POST /time_entries
```

When creating a new time entry [these fields](../time_entries.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"coverage":"...","...":"..."}
```

The response contains [all fields](../time_entries.html#fields) of the created time entry and is similar to the response in [Get a single time entry](../time_entries.html#get-a-single-time-entry)

## Update a time entry

```
PATCH /time_entries/:id
```

When updating a time entry [these fields](../time_entries.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"date":"...","...":"..."}
```

The response contains [all fields](../time_entries.html#fields) of the updated time entry and is similar to the response in [Get a single time entry](../time_entries.html#get-a-single-time-entry)

## Remove a time entry

Remove a time entry with a specific ID.

```
DELETE /time_entries/:id
```

### Response

```
status: 204 No Content
```

## Archive a time entry

```
POST /time_entries/:id/archive
```

Moves a given time entry to the [Archive](../archive/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the time entry.

### Response

```
status: 200 OK
```

```
{"archived":"true","coverage":"...","...":"..."}
```

The response contains [all fields](../time_entries.html#fields) of the archived time entry and is similar to the response in [Get a single time entry](../time_entries.html#get-a-single-time-entry)

## Trash a time entry

```
POST /time_entries/:id/trash
```

Moves a given time entry to the [Trash](../trash/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the time entry.

### Response

```
status: 200 OK
```

```
{"trashed":"true","coverage":"...","...":"..."}
```

The response contains [all fields](../time_entries.html#fields) of the archived time entry and is similar to the response in [Get a single time entry](../time_entries.html#get-a-single-time-entry)

## Restore a time entry

```
POST /time_entries/:id/restore
```

Moves a given time entry from the [Archive](../archive/index.html) or the [Trash](../trash/index.html) back into the active state.
This action requires the Account Administrator or Directory Administrator role in the account of the time entry.

### Response

```
status: 200 OK
```

```
{"coverage":"...","...":"..."}
```

The response contains [all fields](../time_entries.html#fields) of the archived time entry and is similar to the response in [Get a single time entry](../time_entries.html#get-a-single-time-entry)

## Fields

activityID
: *Readonly* **[string](../general/data_types.html)** — The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider. Some examples of activities are standard requests, a high impact incident or a request for information. The Activity ID can be used to support integrations between the billing system of the service provider and the Xurrent account in which the activities are performed.

agreementID
: *Readonly* **[string](../general/data_types.html)** — The Agreement ID is the unique identifier by which all the activities that are performed through the coverage of the SLA are known in the billing system of the service provider. The billing ID can be used to support integrations between the billing system of the service provider and the Xurrent account in which the activities are performed.

charge
: *Readonly* **[decimal](../general/data_types.html)** — For a Time and Materials activity the charge is calculated by multiplying the time spent by the charge rate of the person’s who spent the time based on the selected effort class. For a Fixed Price activity the charge is the amount defined for the fixed price activity in the service offering (of the billable SLA related to the request).

charge\_currency
: *Readonly* **[reference](../general/data_types.html#currency)** — The currency of the charge field value of the time entry.

charge\_rate
: *Readonly* **[decimal](../general/data_types.html)** — Shows the charging rate per hour and is defined by the effort class that was selected when the person registered the time entry.

charge\_type
: *Readonly* **[enum](../general/enumerations/index.html)** — The charge type field defines how the activity is charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

correction
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Correction box is checked when the time entry should be considered a correction for a time entry that was registered for a date that has already been locked.

cost
: *Readonly* **[decimal](../general/data_types.html)**, — The cost field shows cost of the time entry. It is calculated by multiplying the time spent by the cost per hour of the [person’s](../people.html) who spent the time.

cost\_currency
: *Optional* **[enum](../general/enumerations/index.html)** — The currency of the cost field value of the time entry. For valid values, see the list of currencies in the Currency field of the [Account API](../account.html).

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the time entry was created.

customer
: *Required* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Customer field is used to select the organization for which the time was spent. It is automatically set when this time entry is linked to a request, problem, task, or project task.

date
: *Required* **[date](../general/data_types.html)** — The Date field is used to select the date on which the time was spent.

deleted
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Deleted box is automatically checked after the time entry has been deleted. The data of a deleted time entry that is older than 3 months can no longer be retrieved.

description
: *Required* **[string](../general/data_types.html) (max 80)** — The Description field is used to enter a short description of the time spent. This field is available and required only when the Description required box is checked in the selected time allocation.

effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The Effort class field is used to select the effort class that best reflects the type of effort for which time spent is being registered.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the time entry.

note\_id
: *Optional* **[integer](../general/data_types.html)** — The unique ID of the [note](../notes.html) that the time entry is linked to.

note\_nodeID
: *Readonly* **[string](../general/data_types.html)** — The node ID of the [note](../notes.html) that the time entry is linked to. This field cannot be used in the `?fields=` parameter.

organization
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — Always set to the organization to which the person was linked when the time entry was created.

person
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Person field is used to specify the [person](../people.html) who spent the time.

problem
: *Optional* **[reference](../general/data_types.html#references) to [Problem](../problems.html)** — The Problem field shows the problem in which the Time spent field was filled out to cause the time entry to be generated.

project\_task
: *Optional* **[reference](../general/data_types.html#references) to [Task](../tasks.html)** — The Project Task field shows the project task in which the Time spent field was filled out to cause the time entry to be generated.

rateID
: *Readonly* **[string](../general/data_types.html)** — The Rate ID is the unique identifier by which an effort class that is linked to a time entry when an activity was performed through the coverage of the SLA is known in the billing system of the service provider. The effort class represents the type of effort that was performed when working on an activity. Some examples of effort classes are ‘Billable - Normal Hours’, ‘Billable overtime’, ‘Non Billable’ or ‘Senior System Engineer’. The Rate ID can be used to support integrations between the billing system of the service provider and the Xurrent account in which the activities are performed. In the billing system the Rate IDs will be linked to the rates that have been agreed on in the service contract.

request
: *Optional* **[reference](../general/data_types.html#references) to [Request](../requests.html)** — The Request field shows the request in which the Time spent field was filled out to cause the time entry to be generated.

service
: *Required* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the service for which the time was spent. It is automatically set when this time entry is linked to a request, problem, task, or project task.

service\_instance
: *Readonly* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The service instance for which the time was spent. It is automatically set when this time entry is linked to a request, problem, task, or project task.

sla
: *Readonly* **[reference](../general/data_types.html#references) to [Service Level Agreement](../service_level_agreements.html)** — The service level agreement for which the time was spent. It is automatically set when this time entry is linked to a request, problem, task, or project task.

started\_at
: *Optional* **[datetime](../general/data_types.html)** — The date and time the work was started.

task
: *Optional* **[reference](../general/data_types.html#references) to [Task](../tasks.html)** — The Task field shows the task in which the Time spent field was filled out to cause the time entry to be generated.

time\_allocation
: *Optional* **[reference](../general/data_types.html#references) to [Time Allocation](../time_allocations/index.html)** — The Time allocation field is used to select the time allocation on which the time was spent. Only the time allocations that are linked to the person’s organization can be selected.

time\_spent
: *Required* **[integer](../general/data_types.html)**, — The Time spent field is used to specify the number of minutes that was spent on the selected time allocation. The number of minutes is allowed to be negative only when the correction field is set to `true`.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the time entry. If the time entry has no updates it contains the `created_at` value.
