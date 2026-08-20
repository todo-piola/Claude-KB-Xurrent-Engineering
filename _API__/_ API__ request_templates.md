# Request Templates API

- [List request templates](../request_templates.html#list-request-templates)
- [Get a single request template](../request_templates.html#get-a-single-request-template)
- [Create a request template](../request_templates.html#create-a-request-template)
- [Update a request template](../request_templates.html#update-a-request-template)
- [Fields](../request_templates.html#fields)

## List request templates

List all request templates for an account:

```
GET /request_templates
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-14T03:13:49-06:00","category":"rfi","sourceID":null,"updated_at":"2016-03-14T03:13:49-06:00","service":{"name":"Warehouse Management","id":32,"provider":{"name":"Widget Data Center, External IT","id":30}},"subject":"Request for information concerning the Warehouse Management service","id":118,"impact":null,"disabled":false},"..."]
```

The response contains [these fields](../request_templates.html#collection-fields) by default. [Filtering](../request_templates.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of request templates.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/request_templates/disabled`: List all disabled request templates
- `/request_templates/enabled`: List all enabled request templates

### Collection Fields

By default the following [fields](../request_templates.html#fields) will appear in collections of request templates:

`id` `sourceID` `subject` `category` `impact` `service` `created_at` `updated_at`

Obtain a different set of [fields](../request_templates.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../request_templates.html#fields):

`id` `source` `sourceID` `disabled` `subject` `category` `impact` `service` `created_at` `updated_at` `workflow_template`

### Sorting

By default a collection of request templates is sorted **descending** by `id`.

The following [fields](../request_templates.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `category` `impact` `service` `created_at` `updated_at` `times_applied`

## Get a single request template

```
GET /request_templates/:id
```

### Response

```
status: 200 OK
```

```
{"completion_reason":null,"created_at":"2014-12-14T03:13:48-06:00","action_type":"other","description":"Captures formal complaints about the support provided by Widget Data Center. Routes the request to the service desk manager so the dissatisfaction can be addressed with the people involved and used to drive support improvements.","category":"complaint","support_hours":null,"sourceID":null,"workflow_template":null,"workflow_manager":null,"copy_subject_to_requests":true,"end_users":true,"specialists":true,"updated_at":"2014-12-14T03:13:48-06:00","desired_completion":null,"supplier":null,"service":null,"member":{"name":"Khunal Shrestra","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":2},"asset_selection":false,"assign_to_self":false,"subject":"Complaint","localized_subject":"Complaint","id":30,"times_applied":1,"resolution_target":null,"ci":null,"note":null,"time_zone":null,"impact":null,"disabled":false,"team":{"name":"Service Desk","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":2},"status":null,"source":null,"registration_hints":"Explain in the Note field the reason for the dissatisfaction with the support provided by Widget Data Center.","localized_registration_hints":"Explain in the Note field the reason for the dissatisfaction with the support provided by Widget Data Center.","instructions":"Explain to the user that this request will be assigned to Widget Data Center's service desk manager.","ui_extension":null,"urgent":false}
```

The response contains [these fields](../request_templates.html#fields).

## Create a request template

```
POST /request_templates
```

When creating a new request template [these fields](../request_templates.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"assign_to_self":"...","...":"..."}
```

The response contains [all fields](../request_templates.html#fields) of the created request template and is similar to the response in [Get a single request template](../request_templates.html#get-a-single-request-template)

## Update a request template

```
PATCH /request_templates/:id
```

When updating a request template [these fields](../request_templates.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"assign_to_self":"...","...":"..."}
```

The response contains [all fields](../request_templates.html#fields) of the updated request template and is similar to the response in [Get a single request template](../request_templates.html#get-a-single-request-template)

## Fields

action\_type
: *Optional* **[enum](../general/enumerations/index.html)** — The Action type field is used to classify the kind of action this template supports, such as troubleshooting, installation or access provisioning. Valid values are:
: - `troubleshoot`: Troubleshoot - Diagnose and Resolve an Issue
 - `creation`: Creation - Create Something New
 - `modification`: Modification - Change an Existing Item
 - `removal`: Removal - Remove or Delete an Item
 - `replacement`: Replacement - Swap an Item for Another
 - `restoration`: Restoration - Restore to a Previous State
 - `relocation`: Relocation - Move to a Different Location
 - `reporting`: Reporting - Generate or Deliver a Report
 - `information`: Information - Provide Information or Guidance
 - `installation`: Installation - Install New Software or Hardware
 - `upgrade`: Upgrade - Upgrade to a Newer Version
 - `onboarding`: Onboarding - Set Up a New User or Service
 - `offboarding`: Offboarding - Deprovision a User or Service
 - `procurement`: Procurement - Purchase or Acquire an Item
 - `scheduling`: Scheduling - Schedule or Reschedule an Activity
 - `compliance`: Compliance - Ensure Policy or Regulatory Adherence
 - `configuration`: Configuration - Adjust Settings or Parameters
 - `access`: Access - Grant or Revoke Access Rights
 - `renewal`: Renewal - Renew a License or Subscription
 - `transfer`: Transfer - Reassign Ownership or Responsibility
 - `reset`: Reset - Reset a Password or Service State
 - `training`: Training - Request Training or Enablement
 - `other`: Other - Action Not Covered Above

asset\_selection
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Asset Selection box is checked when, after selecting the request template in Self Service, the user needs to be able to select a configuration item in the Asset field..

assign\_after\_workflow\_completion
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether the request will be assigned to the provided team after the workflow is completed. When `false` the request will be completed after the workflow completes.

assign\_to\_self
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Assign to self box is checked to ensure that the person who is registering a new request based on the template is selected in its Member field.

attachments
: *Readonly* **aggregated Attachments**

category
: *Optional* **[enum](../general/enumerations/index.html)** — The Category field is used to select the category that needs to be selected in the Category field of a new request when it is being created based on the template. Valid values are:
: - `incident`: Incident - Request for Incident Resolution
 - `rfc`: RFC - Request for Change
 - `rfi`: RFI - Request for Information
 - `reservation`: Reservation - Request for Reservation
 - `complaint`: Complaint - Request for Support Improvement
 - `compliment`: Compliment - Request for Bestowal of Praise
 - `other`: Other - Request is Out of Scope

ci
: *Optional* **[reference](../general/data_types.html#references) to [Configuration Item](../configuration_items/index.html)** — The Configuration item field is used to select the CI that needs to be copied to the Configuration item field of a new request when it is being created based on the template.

completion\_reason
: *Optional* **[enum](../general/enumerations/index.html)** — The Completion reason field is used to select the completion reason that needs to be selected in the Completion reason field of a new request when it is being created based on the template. Valid values are:
: - `solved`: Solved - Root Cause Analysis Not Required
 - `workaround`: Workaround - Root Cause Not Removed
 - `gone`: Gone - Unable to Reproduce
 - `withdrawn`: Withdrawn - Withdrawn by Requester
 - `conflict`: Conflict - In Conflict with Internal Standard or Policy
 - `unsolvable`: Unsolvable - Unable to Solve

copy\_subject\_to\_requests
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Copy subject to requests box is checked when the subject of the request template needs to become the subject of a request when the template is applied, provided that the Subject field of this request is empty.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the request template was created.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to enter additional context about the purpose of this request template beyond its subject. Adding a clear description improves discoverability. This description is not presented to end users.

desired\_completion
: *Optional* **[integer](../general/data_types.html)** — The Desired completion field is used to enter the number of hours and minutes within which requests that are based on the request template are to be resolved.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the request template may not be used to help register new requests.

effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The effort class that is selected by default, when someone registers time on a request that is based on the request template.

end\_users
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The End users box is checked when the request template is shown to end users in Self Service.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the request template.

impact
: *Optional* **[enum](../general/enumerations/index.html)** — The Impact field is used to select the impact level that needs to be selected in the Impact field of a new request when it is being created based on the template. Valid values are:
: - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

instructions
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Instructions field is used to enter instructions for the support staff who will work on requests that are based on the template.

instructions\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Instructions field.

keywords
: *Optional* **[string](../general/data_types.html) (max 2048)** — The Keywords field contains a comma-separated list of words that can be used to find the request template using search.

localized\_keywords
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — Translated Keywords in the current [language](../index.html#internationalization), defaults to `keywords` in case no translation is provided.

localized\_note
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — Translated Note in the current [language](../index.html#internationalization), defaults to `note` in case no translation is provided.

localized\_registration\_hints
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — Translated Registration hints in the current [language](../index.html#internationalization), defaults to `registration_hints` in case no translation is provided.

localized\_subject
: *Readonly* **[string](../general/data_types.html) (max 255)** — Translated Subject in the current [language](../index.html#internationalization), defaults to `subject` in case no translation is provided.

member
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Member field is used to select the [Person](../people.html) who should be selected in the Member field of a new request when it is being created based on the template.

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to enter the information that needs to be copied to the Note field of a new request when it is being created based on the template.

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Note field.

planned\_effort
: *Optional* **[integer](../general/data_types.html) (max 600000)** — The Planned effort field is used to specify the number of minutes the member is expected to spend working on a request that was created based on the template.

registration\_hints
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Registration hints field is used to enter the information that needs to be displayed after the template has been applied to a new or existing request. This field typically contains step-by-step instructions about how to complete the registration of a request that is based on the template.

registration\_hints\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Registration hints field.

rfc\_type
: *Optional* **[enum](../general/enumerations/index.html)** — The RFC Type field is used to select the type of RFC. It contains the value of the Reference field of a [RFC Type](../rfc_types.html).

service
: *Optional* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the [Service](../services.html) for which the request template is made available.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

specialists
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Specialists box is checked when the request template is shown to Specialists.

status
: *Optional* **[enum](../general/enumerations/index.html)** — The Status field is used to select the status value that needs to be selected in the Status field of a new request when it is being created based on the template. Valid values are:
: - `declined`: Declined
 - `assigned`: Assigned
 - `accepted`: Accepted
 - `in_progress`: In Progress
 - `waiting_for`: Waiting for…
 - `waiting_for_customer`: Waiting for Customer
 - `workflow_pending`: Workflow Pending
 - `completed`: Completed

subject
: *Required* **[string](../general/data_types.html) (max 255)** — The Subject field is used to enter a short description that needs to be copied to the Subject field of a new [Request](../requests.html) when it is being created based on the template.

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the supplier organization that should be selected in the Supplier field of a new request when it is being created based on the template.

support\_hours
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Support hours field is used to select a calendar that is to be used to calculate the desired completion for requests that are based on the request template.

team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Team field is used to select the [Team](../teams.html) that should be selected in the Team field of a new request when it is being created based on the template. Required when `assign_after_workflow_completion` is set to `true`.

time\_zone
: *Optional* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the selected support hours.

times\_applied
: *Readonly* **[integer](../general/data_types.html)** — The number of times the request template is used to create a Request.

translate\_subject
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — Whether the subject of requests created from this template is automatically translated to the language of the viewer. When `false`, the subject is always displayed in its original language.

ui\_extension
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field is used to select the UI extension that is to be added to a new request when it is being created based on the template.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the request template. If the request template has no updates it contains the `created_at` value.

urgent
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Mark as urgent box is checked when a new request that is created based on the template is to be marked as urgent.

workflow\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Workflow manager field is used to relate a [Workflow Manager](../people.html) to the request template. *Required* when a [Workflow Template](../workflow_templates.html) is defined, and the [Service](../services.html) does not define a Workflow Manager.

workflow\_template
: *Optional* **[reference](../general/data_types.html#references) to [Workflow Template](../workflow_templates.html)** — The Workflow template field is used to relate a [Workflow Template](../workflow_templates.html) to the request template. *Required* when the *Status* is set to *Workflow Pending*.
