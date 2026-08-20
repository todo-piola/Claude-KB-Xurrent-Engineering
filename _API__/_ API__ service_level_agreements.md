# Service Level Agreements API

- [List service level agreements](../service_level_agreements.html#list-service-level-agreements)
- [Get a single service level agreement](../service_level_agreements.html#get-a-single-service-level-agreement)
- [Create a service level agreement](../service_level_agreements.html#create-a-service-level-agreement)
- [Update a service level agreement](../service_level_agreements.html#update-a-service-level-agreement)
- [Fields](../service_level_agreements.html#fields)

## List service level agreements

List all service level agreements for an account:

```
GET /slas
```

### Response

```
status: 200 OK
```

```
[{"name":"BlackBerry Standard Smart Phone for Widget Data Center, External IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":145,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},{"name":"BlackBerry Standard Smart Phone for Widget Data Center, Internal IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":146,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},"..."]
```

The response contains [these fields](../service_level_agreements.html#collection-fields) by default. [Filtering](../service_level_agreements.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of service level agreements.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/slas/active`: List all active service level agreements
- `/slas/inactive`: List all inactive service level agreements

### Collection Fields

By default the following [fields](../service_level_agreements.html#fields) will appear in collections of service level agreements:

`service_offering` `id` `sourceID` `name` `status` `created_at` `updated_at`

Obtain a different set of [fields](../service_level_agreements.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../service_level_agreements.html#fields):

`id` `source` `sourceID` `name` `status` `created_at` `updated_at` `service_offering` `service_instance`

### Sorting

By default a collection of service level agreements is sorted **ascending** by `name`.

The following [fields](../service_level_agreements.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`service_offering` `id` `sourceID` `name` `status` `created_at` `updated_at`

## Get a single service level agreement

```
GET /slas/:id
```

### Response

```
status: 200 OK
```

```
{"start_date":"2016-03-03","service_instance":{"name":"ITRP Production","account":{"name":"ITRP Institute","id":"itrp"},"id":1},"name":"Premium Plus IT Resource Planning (ITRP) for Widget Data Center","remarks":null,"notice_date":null,"created_at":"2016-03-14T03:10:43-06:00","coverage":"service_instances","sourceID":null,"updated_at":"2016-03-14T03:10:43-06:00","account":{"name":"ITRP Institute","id":"itrp"},"id":5,"expiry_date":null,"service_offering":{"name":"Premium Plus IT Resource Planning (ITRP)","service":{"name":"IT Resource Planning (ITRP)","account":{"name":"ITRP Institute","id":"itrp"},"id":1,"provider":{"name":"ITRP Institute, Inc.","account":{"name":"ITRP Institute","id":"itrp"},"id":1}},"account":{"name":"ITRP Institute","id":"itrp"},"id":4},"customer_rep":{"name":"Howard Tanner","id":5},"customer":{"name":"Widget Data Center, External IT","id":30},"status":"active","source":null,"service_level_manager":{"name":"Frederieke Winkler Prins","account":{"name":"ITRP Institute","id":"itrp"},"id":9}}
```

The response contains [these fields](../service_level_agreements.html#fields).

## Create a service level agreement

```
POST /slas
```

When creating a new service level agreement [these fields](../service_level_agreements.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"coverage":"...","...":"..."}
```

The response contains [all fields](../service_level_agreements.html#fields) of the created service level agreement and is similar to the response in [Get a single service level agreement](../service_level_agreements.html#get-a-single-service-level-agreement)

## Update a service level agreement

```
PATCH /slas/:id
```

When updating a service level agreement [these fields](../service_level_agreements.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"coverage":"...","...":"..."}
```

The response contains [all fields](../service_level_agreements.html#fields) of the updated service level agreement and is similar to the response in [Get a single service level agreement](../service_level_agreements.html#get-a-single-service-level-agreement)

## Fields

activityID\_low
: *Optional* **[string](../general/data_types.html)** — Represents the activityID for low incidents. The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider.

activityID\_medium
: *Optional* **[string](../general/data_types.html)** — Represents the activityID for medium incidents. The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider.

activityID\_high
: *Optional* **[string](../general/data_types.html)** — Represents the activityID for high incidents. The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider.

activityID\_top
: *Optional* **[string](../general/data_types.html)** — Represents the activityID for top incidents. The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider.

activityID\_rfc
: *Optional* **[string](../general/data_types.html)** — Represents the activityID for RFCs. The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider.

activityID\_rfi
: *Optional* **[string](../general/data_types.html)** — Represents the activityID for RFIs. The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider.

activityID\_case
: *Optional* **[string](../general/data_types.html)** — Represents the activityID for case. The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider.

agreementID
: *Optional* **[string](../general/data_types.html)** — The Agreement ID is the unique identifier by which all the activities that are performed through the coverage of the SLA are known in the billing system of the service provider.

attachments
: *Readonly* **aggregated Attachments**

coverage
: *Optional* **[enum](../general/enumerations/index.html)** — The Coverage field is used to specify how people who are to be covered by the service level agreement are to be selected. Valid values are:
: - `customer_account`: All People of Customer Account
 - `organizations_and_descendants`: People of the Following Organization(s) and Their Descendants
 - `organizations`: People of the Following Organization(s)
 - `sites`: People of the Following Site(s)
 - `organizations_and_sites`: People of an Organization and Site from the Following
 - `people`: People Selected Below
 - `coverage_groups`: People of the Following Coverage Group(s)
 - `cis_of_service_instance`: People Using CIs of the Service Instance
 - `service_instances`: Members of Support Teams of the Following Service Instances
 - `skill_pools`: Members of the Following Skill Pool(s)

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the service level agreement was created.

customer
: *Required* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Customer field is used to select the [Organization](../organizations.html) that pays for the service level agreement.

customer\_account
: *Optional* **[reference](../general/data_types.html#references) to [Account](../account.html)** — This field is used to specify the Account which service level managers are allowed to update the parts of the SLA that are intended to be maintained by the service level managers of the customer.
 More importantly, this field is used to specify whether specialists of the customer are allowed to see the requests that include this SLA in their Affected SLAs section.

customer\_rep
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — deprecated field containing the first customer representative of the SLA. Please use the specific [customer representatives endpoint](customer_representatives.html) to retrieve and manipulate the SLA’s customer representatives. When this field is used to update an existing SLA, all customer representatives that are linked to this SLA will be replaced by the new customer representative.

customer\_representative\_ids
: *Writeonly* **[references](../general/data_types.html#references) to [People](../people.html)** — This field is used to specify the full list of customer representatives of the SLA. In general, it is preferred to use the specific [customer representatives endpoint](customer_representatives.html) to retrieve and manipulate the SLA’s customer representatives. However, since it is required to specify at least one customer representative when a SLA is activated, the `customer_representative_ids` field must be used when creating a new, active, SLA.

expiry\_date
: *Optional* **[date](../general/data_types.html)** — The Expiry date field is used to specify the date through which the service level agreement (SLA) will be active. The SLA expires at the end of this day if it is not renewed before then. When the SLA has expired, its status will automatically be set to “Expired”.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the service level agreement.

name
: *Required* **[string](../general/data_types.html) (max 160)** — The Name field is used to enter the name of the service level agreement.

notice\_date
: *Optional* **[date](../general/data_types.html)** — The Notice date field is used to specify the last day on which the service provider organization can still be contacted to terminate the service level agreement (SLA) to ensure that it expires on the intended expiry date. The Notice date field is left empty, and the Expiry date field is filled out, when the SLA is to expire on a specific date and no notice needs to be given to terminate it.

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the service level agreement that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Remarks field.

service\_instance
: *Optional* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The Service instance field is used to select the [Service Instance](../service_instances/index.html) that will be used to provide the service to the customer of the service level agreement. Only service instances that are linked to the same service as the selected service offering can be selected.

service\_level\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Service level manager field is used to select the person of the service provider organization who acts as the service level manager for the customer of the service level agreement.

service\_offering
: *Required* **[reference](../general/data_types.html#references) to [Service Offering](../service_offerings/index.html)** — The Service offering field is used to select the [Service Offering](../service_offerings/index.html) that specifies the conditions that apply to the service level agreement.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_date
: *Optional* **[date](../general/data_types.html)** — The Start date field is used to specify the first day during which the service level agreement (SLA) is active.

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `being_prepared` — The Status field displays the current status of the service level agreement (SLA). Valid values are:
: - `being_prepared`: Being Prepared
 - `scheduled_for_activation`: Scheduled for Activation
 - `active`: Active
 - `expired`: Expired

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the service level agreement. If the service level agreement has no updates it contains the `created_at` value.

use\_knowledge\_from\_service\_provider
: *Optional* **[boolean](../general/data_types.html)** — The Use knowledge from service provider box is checked when the knowledge articles for the service instance that is selected in the Service instance field need to be made available to the people who are covered by an active SLA for the service instances selected in the Service instances table field.
