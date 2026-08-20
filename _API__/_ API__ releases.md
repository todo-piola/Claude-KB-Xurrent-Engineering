# Releases API

- [List releases](../releases.html#list-releases)
- [Get a single release](../releases.html#get-a-single-release)
- [Create a release](../releases.html#create-a-release)
- [Update a release](../releases.html#update-a-release)
- [Archive a release](../releases.html#archive-a-release)
- [Trash a release](../releases.html#trash-a-release)
- [Restore a release](../releases.html#restore-a-release)
- [Fields](../releases.html#fields)

## List releases

List all releases for an account:

```
GET /releases
```

### Response

```
status: 200 OK
```

```
[{"completion_target_at":"2016-06-14T15:00:00-05:00","status":"implementation","created_at":"2016-04-27T05:24:00-05:00","updated_at":"2016-05-31T18:53:31-05:00","subject":"Automate exchange rate updates in Expense Reporting","id":294,"sourceID":null,"completed_at":null,"impact":"none"},"..."]
```

The response contains [these fields](../releases.html#collection-fields) by default. [Filtering](../releases.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of releases.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/releases/completed`: List all completed releases
- `/releases/open`: List all open releases
- `/releases/managed_by_me`: List all releases which manager is the API user

### Collection Fields

By default the following [fields](../releases.html#fields) will appear in collections of releases:

`id` `sourceID` `subject` `impact` `status` `completion_target_at` `completed_at` `created_at` `updated_at`

Obtain a different set of [fields](../releases.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../releases.html#fields):

`id` `source` `sourceID` `subject` `impact` `status` `completion_target_at` `completed_at` `created_at` `updated_at`

### Sorting

By default a collection of releases is sorted **descending** by `id`.

The following [fields](../releases.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `impact` `status` `completion_target_at` `completed_at` `created_at` `updated_at`

### Response

The response is similar to the response in [List releases](../releases.html#list-releases)

## Get a single release

```
GET /releases/:id
```

### Response

```
status: 200 OK
```

```
{"completion_target_at":"2016-06-14T15:00:00-05:00","status":"implementation","created_at":"2016-04-27T05:24:00-05:00","updated_at":"2016-05-31T18:53:31-05:00","subject":"Automate exchange rate updates in Expense Reporting","id":294,"sourceID":null,"completed_at":null,"impact":"none","completion_reason":null,"manager":{"id":53,"name":"Frank Watson","account":{"id":"widget","name":"Widget International"}},"source":null}
```

The response contains [these fields](../releases.html#fields).

## Create a release

```
POST /releases
```

When creating a new release [these fields](../releases.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"subject":"...","...":"..."}
```

The response contains [all fields](../releases.html#fields) of the created release and is similar to the response in [Get a single release](../releases.html#get-a-single-release)

## Update a release

```
PATCH /releases/:id
```

When updating a release [these fields](../releases.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"subject":"...","...":"..."}
```

The response contains [all fields](../releases.html#fields) of the updated release and is similar to the response in [Get a single release](../releases.html#get-a-single-release)

## Archive a release

```
POST /releases/:id/archive
```

Moves a given release to the [Archive](../archive/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the release.

### Response

```
status: 200 OK
```

```
{"archived":"true","subject":"...","...":"..."}
```

The response contains [all fields](../releases.html#fields) of the archived release and is similar to the response in [Get a single release](../releases.html#get-a-single-release)

## Trash a release

```
POST /releases/:id/trash
```

Moves a given release to the [Trash](../trash/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the release.

### Response

```
status: 200 OK
```

```
{"trashed":"true","subject":"...","...":"..."}
```

The response contains [all fields](../releases.html#fields) of the archived release and is similar to the response in [Get a single release](../releases.html#get-a-single-release)

## Restore a release

```
POST /releases/:id/restore
```

Moves a given release from the [Archive](../archive/index.html) or the [Trash](../trash/index.html) back into the view of “Completed Releases”.
This action requires the Account Administrator or Directory Administrator role in the account of the release.

### Response

```
status: 200 OK
```

```
{"subject":"...","...":"..."}
```

The response contains [all fields](../releases.html#fields) of the archived release and is similar to the response in [Get a single release](../releases.html#get-a-single-release)

## Fields

attachments
: *Readonly* **aggregated Attachments**
: Use [Releases - Notes API](notes/index.html) to get note attachments.

completed\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Completed at field is automatically set to the date and time at which the release is set to the status “Completed”.

completion\_reason
: *Readonly* **[enum](../general/enumerations/index.html)** — The Completion reason field is automatically set based on the completion reason of the release’s workflows. Possible values are:
: - `withdrawn`: Withdrawn - Withdrawn by Requester
 - `rejected`: Rejected - Rejected by Approver
 - `rolled_back`: Rolled Back - Original Environment Restored
 - `failed`: Failed - No Requirements Met
 - `partial`: Partial - Not All Requirements Met
 - `disruptive`: Disruptive - Caused Service Disruption
 - `complete`: Complete - All Requirements Met

completion\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Completion target field shows the target date and time of the last task of the workflows that are related to the release.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the release was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the release.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the release.

impact
: *Readonly* **[enum](../general/enumerations/index.html)** — The Impact field shows the maximum impact level that is selected in the tasks of the workflows that are related to the release. This indicates the maximum extent to which a “service instance”:/help/service\_instance will be impacted by the implementation of the release. Possible values are:
: - `none`: None - Service Not Degraded
 - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

manager
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)**, default: authenticated person — The Manager field is used to select the [Person](../people.html) who is responsible for coordinating the implementation of the release. The person must have the release Manager role.

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to provide a high-level description of the result that should be accomplished by the implementation of the release’s workflows. It is also used to add any information that could prove useful for anyone affected by the release.
: The Note field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Note field.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

status
: *Readonly* **[enum](../general/enumerations/index.html)** — The Status field is automatically set based on the status of the release’s workflows. Possible values are:
: - `registered`: Registered
 - `risk_and_impact`: Risk & Impact — *deprecated: replaced by `in_progress`*
 - `approval`: Approval — *deprecated: replaced replaced by `in_progress`*
 - `implementation`: Implementation — *deprecated: replaced by `in_progress`*
 - `in_progress`: In Progress
 - `progress_halted`: Progress Halted
 - `completed`: Completed

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the objective of the release.

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the release.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the release. If the release has no updates it contains the `created_at` value.
