# Requests API

- [List requests](../requests.html#list-requests)
- [Get a request](../requests.html#get-a-request)
- [Create a request](../requests.html#create-a-request)
- [Update a request](../requests.html#update-a-request)
- [Archive a request](../requests.html#archive-a-request)
- [Trash a request](../requests.html#trash-a-request)
- [Restore a request](../requests.html#restore-a-request)
- [Fields](../requests.html#fields)

## List Requests

List all requests for an account:

```
GET /requests
```

### Response

```
status: 200 OK
```

```
[{"service_instance":{"name":"Windows for Sales Tracking Production","id":126},"completed_at":null,"created_at":"2016-03-14T02:56:11-06:00","category":"rfc","sourceID":null,"updated_at":"2016-03-14T03:14:11-06:00","grouped_into":null,"member":{"name":"Barney Turban","id":58},"subject":"Add memory to Sales Tracking production server cluster","id":70470,"impact":null,"team":{"name":"Windows Servers","id":14},"status":"assigned","next_target_at":"best_effort"},"..."]
```

The response contains [these fields](../requests.html#collection-fields) by default. [Filtering](../requests.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of requests.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/requests/completed`: List all completed requests
- `/requests/open`: List all open requests
- `/requests/requested_by_or_for_me`: List all requests which requested by person or requested for person is the API user
- `/requests/assigned_to_my_team`: List all requests that are assigned to one of the teams that the API user is a member of
- `/requests/assigned_to_me`: List all requests that are assigned to the API user
- `/requests/waiting_for_me`: List all requests which requested by person is the API user and which status is `Waiting for Customer`
- `/requests/problem_management_review`: List all requests that were completed less than 6 months ago and which are linked to a service instance of a service for which the API user is the problem manager
- `/requests/sla_accountability`: List all requests that one of the teams of the API user can be held accountable for

### Collection Fields

By default the following [fields](../requests.html#fields) will appear in collections of requests:

`id` `sourceID` `subject` `category` `impact` `status` `next_target_at` `completed_at` `team` `member` `grouped_into` `service_instance` `created_at` `updated_at`

Obtain a different set of [fields](../requests.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../requests.html#fields):

`id` `source` `sourceID` `subject` `category` `impact` `status` `workflow` `next_target_at`
`completed_at` `created_by` `grouping` `grouped_into` `knowledge_article` `requested_by` `requested_for` `service_instance`
`supplier_requestID` `created_at` `updated_at` `team` `member` `template` `major_incident_status` `organization`

### Sorting

By default a collection of requests is sorted **descending** by `id`.

The following [fields](../requests.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `category` `impact` `status` `next_target_at` `completed_at` `team` `member` `service_instance` `created_at` `updated_at`

### Response

The response is similar to the response in [List requests](../requests.html#list-requests)

## Get a Request

```
GET /requests/:id
```

### Response

```
status: 200 OK
```

```
{"service_instance":{"name":"Data Center Rack Space","id":29},"organization":{"id":44,"name":"Widget Data Center, External IT"},"completion_reason":"solved","closure_code":"hardware_issue_resolved","completed_at":"2014-03-04T02:14:00-06:00","desired_completion_at":"2014-03-04T03:00:00-06:00","requested_by":{"name":"Patrick Spratt","id":56},"created_by":{"name":"Patrick Spratt","id":56},"created_at":"2009-02-02T12:18:00-06:00","category":"rfc","sourceID":null,"downtime_start_at":null,"updated_at":"2016-03-14T03:14:13-06:00","supplier":null,"resolution_target_at":null,"requester_resolution_target_at":null,"new_assignment":false,"grouping":"none","grouped_into":null,"member":{"name":"Carla Cluster","id":54},"resolution_duration":null,"supplier_requestID":null,"subject":"Add new rack in data center","response_target_at":null,"id":68673,"requested_for":{"name":"Patrick Spratt","id":56},"problem":null,"workflow":{"id":238,"subject":"Install new rack"},"project":null,"ci":null,"downtime_end_at":null,"impact":null,"team":{"name":"Unix Servers","id":13},"status":"completed","source":"4me Self Service","next_target_at":"no_target","template":null,"custom_fields":null,"waiting_until":null,"reviewed":true,"satisfaction":"satisfied","knowledge_article":null,"urgent":false,"addressed":false,"feedback":{"requested_by":{"satisfied_url":"https://widget.xurrent.com/requests/68673/2sii015q/149/yes","dissatisfied_url":"https://widget.xurrent.com/requests/68673/2sii015q/149/no"}}}
```

The response contains [these fields](../requests.html#fields).

## Create a Request

```
POST /requests
```

When creating a new request [these fields](../requests.html#fields) are available.

Requests can also be created using the [Mail API](mail.html). In addition, a specific [Events API](events.html) is available to support monitoring tools that prefer sending HTTP requests rather than email.

### Response

```
status: 201 Created
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](../requests.html#fields) of the created request and is similar to the response in [Get a single request](../requests.html#get-a-single-request)

## Update a Request

```
PATCH /requests/:id
```

When updating a request [these fields](../requests.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](../requests.html#fields) of the updated request and is similar to the response in [Get a single request](../requests.html#get-a-single-request)

## Archive a Request

```
POST /requests/:id/archive
```

Moves a given request to the [Archive](../archive/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the request.

### Response

```
status: 200 OK
```

```
{"archived":"true","category":"...","...":"..."}
```

The response contains [all fields](../requests.html#fields) of the archived request and is similar to the response in [Get a single request](../requests.html#get-a-single-request)

## Trash a Request

```
POST /requests/:id/trash
```

Moves a given request to the [Trash](../trash/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the request.

### Response

```
status: 200 OK
```

```
{"trashed":"true","category":"...","...":"..."}
```

The response contains [all fields](../requests.html#fields) of the archived request and is similar to the response in [Get a single request](../requests.html#get-a-single-request)

## Restore a Request

```
POST /requests/:id/restore
```

Moves a given request from the [Archive](../archive/index.html) or the [Trash](../trash/index.html) back into the view of “Completed Requests”.
This action requires the Account Administrator or Directory Administrator role in the account of the request.

### Response

```
status: 200 OK
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](../requests.html#fields) of the archived request and is similar to the response in [Get a single request](../requests.html#get-a-single-request)

## Fields

Note: if a request is visible in multiple accounts, the following fields in the response of an API request are account specific,
which means that the value can be different for the same request depending on the account that has been specified in the `X-Xurrent-Account` header of the API call:

`assignment_count` `completed_at` `completion_reason` `created_at` `major_incident_status` `member` `next_target_at` `reopen_count` `status` `supplier` `supplier_requestID` `team`

addressed
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — When the Satisfaction field of the request is set to ‘Dissatisfied’, a person who has the Service Desk Manager role, can check the Addressed box to indicate that the requester has been conciliated.

agile\_board
: *Optional* **[reference](../general/data_types.html#references) to [Agile Board](../agile_boards/index.html)** — The Agile board on which the request is placed.

agile\_board\_column
: *Optional* **[reference](../general/data_types.html#references) to [Agile Board Column](../agile_boards/columns.html)** — The column of the agile board on which the request is placed.

agile\_board\_column\_position
: *Optional* **[integer](../general/data_types.html)** — The Position field is used to specify the position of the request,
 relative to the other items within the column of the agile board. The topmost item has position 1.

assignment\_count
: *Readonly* **[integer](../general/data_types.html)** — The Assignment count field is automatically set to the number of times that the Team field of the request has been set to a [Team](../teams.html) that is registered in the [Account](../index.html#multiple-accounts) from which the request data is retrieved.

attachments
: *Readonly* **aggregated Attachments**
: Use [Requests - Notes API](notes/index.html) to get note attachments.

category
: *Required* **[enum](../general/enumerations/index.html)** — The Category field is used to select the category of the request. Valid values are:
: - `incident`: Incident - Request for Incident Resolution
 - `rfc`: RFC - Request for Change
 - `rfi`: RFI - Request for Information
 - `reservation`: Reservation - Request for Reservation
 - `order`: Order - Request for Purchase
 - `fulfillment`: Fulfillment - Request for Order Fulfillment
 - `complaint`: Complaint - Request for Support Improvement
 - `compliment`: Compliment - Request for Bestowal of Praise
 - `other`: Other - Request is Out of Scope

ci
: *Optional* **[reference](../general/data_types.html#references) to [Configuration Item](../configuration_items/index.html)** — The Configuration item field is used to relate a [CI](../configuration_items/index.html) to the request. When this field is used to update an existing request, all configuration items that are linked to this request will be replaced by the new configuration item.
: Multiple configuration items can be added to, or removed from, a request using the [Requests - Configuration Items API](cis/index.html).

checked\_items
: *Optional* **array of string** — The names of the checklist items that are checked within the instructions field.

completed\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Completed at field is automatically set to the date and time at which the request is saved with the status “Completed”.

completion\_reason
: *Optional* **[enum](../general/enumerations/index.html)** — The Completion reason field is used to select the appropriate completion reason for the request when it has been completed. Valid values are:
: - `solved`: Solved - Root Cause Analysis Not Required
 - `workaround`: Workaround - Root Cause Not Removed
 - `gone`: Gone - Unable to Reproduce
 - `duplicate`: Duplicate - Same as Another Request of Customer
 - `withdrawn`: Withdrawn - Withdrawn by Requester
 - `no_reply`: No Reply - No Reply Received from Customer
 - `rejected`: Rejected - Rejected by Approver
 - `conflict`: Conflict - In Conflict with Internal Standard or Policy
 - `declined`: Declined - Declined by Service Provider
 - `unsolvable`: Unsolvable - Unable to Solve

closure\_code
: *Optional* **[enum](../general/enumerations/index.html)** — The Closure code field is used to select the closure code that indicates how the request was resolved or closed. It contains the value of the Reference field of a [Closure Code](../closure_codes/index.html).

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the request was created.

created\_by
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Created by field is automatically set to the person who submitted the request.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the related request template.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

downtime\_end\_at
: *Optional* **[datetime](../general/data_types.html)** — The Downtime end field is used to specify the actual date and time at which the service became available again.

downtime\_start\_at
: *Optional* **[datetime](../general/data_types.html)** — The Downtime start field is used to specify the actual date and time at which the service outage started.

desired\_completion\_at
: *Optional* **[datetime](../general/data_types.html)** — The Desired completion field can be set to the date and time that has been agreed on for the completion of the request. The desired completion overwrites the automatically calculated resolution target of any affected SLA that is related to the request when the desired completion is later than the affected SLA’s resolution target. By default, the person selected in the Requested by field receives a notification based on the ‘Desired Completion Set for Request’ email template whenever the value in the Desired completion field is set, updated or removed.

feedback
: *Readonly* **[hash](../general/data_types.html)** — Hash containing the `satisfied_url` and the `dissatisfied_url` of the `requested_for`. In case the `requested_by` is different form the `requested_for`, the satisfaction link of the `requested_by` are also included. Feedback is `null` in case no feedback for the request can be provided at this time.

feedback\_on\_knowledge\_article
: *Readonly* **[reference](../general/data_types.html#references) to [Knowledge Article](../knowledge_articles.html)** — The knowledge article that this request provides feedback on.

grouped\_into
: *Optional* **[reference](../general/data_types.html#references) to [Request](../requests.html)** — The Grouped into field displays the request group that is used to group the requests that have been submitted for the resolution of exactly the same incident, for the implementation of exactly the same change, for the provision of exactly the same information, etc.

grouping
: *Readonly* **[enum](../general/enumerations/index.html)**, default: `none` — Valid values are:
: - `none`: None
 - `group`: Group
 - `grouped`: Grouped

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the request.

impact
: *Optional* **[enum](../general/enumerations/index.html)** — The Impact field is used to select the extent to which the service instance is impacted. Required when the category is Incident. Valid values are:
: - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

internal\_note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Internal note field is used to provide information that is visible only for people who have the Auditor, Specialist or Account Administrator role of the account for which the internal note is intended. The `X-Xurrent-Account header` can be included in an API PATCH request to add an internal note for a specific account (see [Multiple Accounts](../index.html#multiple-accounts)).
: The Internal note field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

internal\_note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Internal Note field.

knowledge\_article
: *Optional* **[reference](../general/data_types.html#references) to [Knowledge Article](../knowledge_articles.html)** — The Knowledge Article field is used to relate a [KnowledgeArticle](../knowledge_articles.html) to the request. When this field is used to update an existing request, all knowledge articles that are linked to this request will be replaced by the new knowledge article.

major\_incident\_status
: *Optional* **[enum](../general/enumerations/index.html)** — The Major Incident Status field is used to indicate the status in the major incident management process. Valid values are:
: - `proposed`: Proposed
 - `rejected`: Rejected
 - `accepted`: Accepted
 - `resolved`: Resolved
 - `canceled`: Canceled

member
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Member field is used to select the person to whom the request is to be assigned.

new\_assignment
: *Readonly* **[boolean](../general/data_types.html)**, default: `true` — The New assignment field is set to `true` when the request’s status is ‘Assigned’ or ‘Declined’.

next\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Next target field value is empty when the status of the request is ‘Completed’. The next target equals the response target when a response target exists and the response target is less than the desired completion. Otherwise, the next target equals the desired completion when a desired completion exists. Otherwise, if the status is ‘Waiting for Customer’ the next target is `clock_stopped` when an affected SLA is linked to the request which Accountability field is set to `provider` or `supplier`. Otherwise, if the status is ‘Waiting for Customer’ the next target is `best_effort`. Otherwise the next target is the resolution target when a resolution target exists. In all other cases, the next target is `best_effort`.

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to provide any additional information that could prove useful for resolving the request and/or to provide a summary of the actions that have been taken since the last entry.
: The Note field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Note field.

organization
: *Readonly* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Organization field is automatically set when the request is saved for the first time to the organization that the person, who is selected in the Requested for field, belongs.

planned\_effort
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field is used to specify the number of minutes the member is expected to spend working on the request.

problem
: *Optional* **[reference](../general/data_types.html#references) to [Problem](../problems.html)** — The Problem field is used to link the request to a problem.

product\_backlog
: *Optional* **[reference](../general/data_types.html#references) to [Product Backlog](../product_backlogs/index.html)** — The Product backlog field is used to place the request on a product backlog. When a request is placed on a product backlog without specifying a `product_backlog_position` it is placed at the bottom of the product backlog.

product\_backlog\_position
: *Optional* **[integer](../general/data_types.html)** — The Product backlog position field is used to determine the relative position of the request on the product backlog (the top most item has position 1). When a request is placed on a product backlog without specifying a `product_backlog_position` it is placed at the bottom of the product backlog.

project
: *Optional* **[reference](../general/data_types.html#references) to [Project](../projects/index.html)** — The Project field is used to link the request to a project.

provider\_not\_accountable
: *Optional* **[boolean](../general/data_types.html)** — The Provider not accountable field value is used to indicate when the provider is currently not to be accountable.

provider\_was\_not\_accountable
: *Readonly* **[boolean](../general/data_types.html)** — The Provider was not accountable field value is automatically set to `true` when the provider has at any point in time indicated not to be accountable.

reopen\_count
: *Readonly* **[integer](../general/data_types.html)** — The Reopen count field is automatically set to the number of times that the status of the request has changed from ‘Completed’ to a different value in the [Account](../index.html#multiple-accounts) from which the request data is retrieved.

reservation
: *Optional* **[reference](../general/data_types.html#references) to [Reservation](../reservations.html)** — The Reservations field is used to link the request to a reservation.

resolution\_duration
: *Readonly* **[integer](../general/data_types.html)** — The number of minutes it took to complete this request, which is calculated as the difference between the `created_at` and `completed_at` values.

resolution\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Resolution target field automatically indicates when the current assignment team needs to have completed the request. The target displayed in this field is the most stringent resolution target of the affected SLAs that are related to the request and for which the current assignment team is responsible.

response\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Response target field automatically indicates when the current assignment team needs to have responded to the request. The target displayed in this field is the most stringent response target of the affected SLAs that are related to the request and for which the current assignment team is responsible.

requested\_by
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Requested by field is used to select the person who submitted the request.

requested\_for
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Requested for field is used to select the person for whom the request was submitted. The person selected in the Requested by field is automatically selected in this field, but another person can be selected if the request is submitted for another person.

requester\_resolution\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Requester resolution target field is automatically set to the most stringent resolution target of the request’s affected SLAs, which Accountability field is not set to `sla_not_affected` and which are linked to an SLA for which the person who is selected in the Requested for field has coverage.

reviewed
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — A request can be marked as reviewed by the problem manager of the service of the service instance that is linked to the request. Marking a request as reviewed excludes it from the ‘Requests for Problem Identification’ view.
: This field is automatically set to `true` when the Service instance field is empty, when the request is linked to a problem or workflow, or when the Grouping field is set to `grouped`. This field is also set to `true` when the completion\_reason is `solved` and the impact is different from `top`.

rfc\_type
: *Optional* **[enum](../general/enumerations/index.html)** — The RFC Type field is used to select the type of RFC. It contains the value of the Reference field of a [RFC Type](../rfc_types.html).

satisfaction
: *Readonly* **[enum](../general/enumerations/index.html)** — The Satisfaction field is set when a requester uses the hyperlinks defined in the ‘Request Set to Completed’ email template to indicate whether or not he/she is satisfied with the manner in which a request has been handled. Valid values, apart from the default `null`, are:
: - `dissatisfied`: Dissatisfied
 - `satisfied`: Satisfied

 It is also possible to set the value of this field via the [Request Satisfaction API](satisfaction.html).

service\_instance
: *Optional* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The Service instance field is used to select the [Service Instance](../service_instances/index.html) in which the cause of the incident resides, for which the workflow is requested, or about which information is needed.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `assigned` — The Status field is used to select the current status of the request. Valid values are:
: - `declined`: Declined
 - `on_backlog`: On Backlog
 - `assigned`: Assigned
 - `accepted`: Accepted
 - `in_progress`: In Progress
 - `waiting_for`: Waiting for…
 - `waiting_for_customer`: Waiting for Customer
 - `reservation_pending`: Reservation Pending
 - `workflow_pending`: Workflow Pending
 - `project_pending`: Project Pending
 - `completed`: Completed

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description of the request.

summary
: *Readonly* **[text](../general/data_types.html)** - AI Summary created for the current request account. Be aware that the AI summary might not always be fully up to date, because it can take a while for an AI Summary to be generated after adding a new note.

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the supplier organization that has been asked to assist with the request. The supplier organization is automatically selected in this field after a service instance has been selected that is provided by an external service provider organization.

supplier\_requestID
: *Optional* **[string](../general/data_types.html) (max 255)** — The Supplier request ID field is used to enter the identifier under which the request has been registered at the supplier organization. If the supplier provided a link to the request, enter the entire URL in this field.

support\_domain
: Used to specify the support domain account ID in which the request is to be registered. This parameter needs to be specified when the current user’s Person record is registered in a directory account. The ID of a Xurrent account can be found in the ‘Account Overview’ section of the Settings console.

task
: *Optional* **[reference](../general/data_types.html#references) to [Task](../tasks.html)** — The Task field is visible only when the request was automatically generated by a task. When visible, this field contains the task that caused the request to be generated.

team
: *Required* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Team field is used to select the [Team](../teams.html) to which the request is to be assigned. By default, the first line team of the service instance that is related to the request will be selected. If a first line team has not been specified for the service instance, the support team of the service instance will be selected instead.

template
: *Optional* **[reference](../general/data_types.html#references) to [Request Template](../task_templates.html)** — The Template field contains the link to the request template that was last applied to the request.

time\_spent
: *Optional* **[integer](../general/data_types.html)** — The Time spent field is used to enter the time that you have spent working on the request since you started to work on it or, if you already entered some time for this request, since you last added your time spent in it.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

time\_spent\_effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The Effort class field is used to select the effort class that best reflects the type of effort for which time spent is being registered.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the request. If the request has no updates it contains the `created_at` value.

urgent
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — When the request has been marked as urgent, the Urgent field is set to `true`.

waiting\_until
: *Optional* **[datetime](../general/data_types.html)** — The Waiting until field is used to specify the date and time at which the status of the request is to be updated from `waiting_for` to `assigned`. This field is available only when the Status field is set to `waiting_for`.

workflow
: *Optional* **[reference](../general/data_types.html#references) to [Workflow](../workflows.html)** — The Workflow field is used to link the request to a workflow.
