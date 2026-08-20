# First Line Support Agreements API

- [List first line support agreements](index.html#list-support-agreements)
- [Get a single first line support agreement](index.html#get-a-single-first-line-support-agreement)
- [Create a first line support agreement](index.html#create-a-first-line-support-agreement)
- [Update a first line support agreement](index.html#update-a-first-line-support-agreement)
- [Fields](index.html#fields)

## List first line support agreements

List all first line support agreements for an account:

```
GET /flsas
```

### Response

```
status: 200 OK
```

```
[{"name":"FLSA0001029 First line support agreement for Widget Data Center","created_at":"2016-03-14T03:10:49-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:49-06:00","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":3,"status":"active","provider":{"name":"VirtualSupport, Ltd.","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":2}},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of first line support agreements.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/flsas/active`: List all active first line support agreements
- `/flsas/inactive`: List all inactive first line support agreements

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of first line support agreements:

`provider` `id` `sourceID` `name` `status` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`provider` `id` `source` `sourceID` `name` `status` `created_at` `updated_at`

### Sorting

By default a collection of first line support agreements is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`provider` `id` `sourceID` `name` `status` `created_at` `updated_at`

## Get a single first line support agreement

```
GET /flsas/:id
```

### Response

```
status: 200 OK
```

```
{"target_details":null,"start_date":"2009-01-01","name":"FLSA0001029 First line support agreement for Widget Data Center","remarks":null,"notice_date":"2017-12-31","created_at":"2016-03-14T03:10:49-06:00","support_hours":{"name":"24x7 (Monday through Sunday)","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":71},"sourceID":null,"updated_at":"2016-03-14T03:10:49-06:00","service_desk_team":{"name":"Service Desk","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":2},"account":{"name":"VirtualSupport","id":"virtualsupport"},"id":3,"expiry_date":null,"charges":"Customer is charged $10 per request registered by VirtualSupport. In addition, customer is charged $10 per request completed by VirtualSupport.","time_zone":"Mumbai","first_call_resolutions":60,"customer_rep":{"name":"Howard Tanner","id":5},"customer":{"name":"Widget Data Center","id":5},"status":"active","source":null,"provider":{"name":"VirtualSupport, Ltd.","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":2}}
```

The response contains [these fields](index.html#fields).

## Create a first line support agreement

```
POST /flsas
```

When creating a new first line support agreement [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"charges":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created first line support agreement and is similar to the response in [Get a single first line support agreement](index.html#get-a-single-first-line-support-agreement)

## Update a first line support agreement

```
PATCH /flsas/:id
```

When updating a first line support agreement [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"charges":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated first line support agreement and is similar to the response in [Get a single first line support agreement](index.html#get-a-single-first-line-support-agreement)

## Fields

attachments
: *Readonly* **aggregated Attachments**

charges
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Charges field is used to describe the amounts that the customer will be charged for the first line support agreement. These can be recurring as well as one-off charges.

charges\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Charges field.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the first line support agreement was created.

customer
: *Required* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Customer field is used to select the [Organization](../organizations.html) that pays for the first line support agreement.

customer\_rep
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)**

expiry\_date
: *Optional* **[date](../general/data_types.html)** — The Expiry date field is used to specify the date through which the first line support agreement (FLSA) will be active. The FLSA expires at the end of this day if it is not renewed before then. When the FLSA has expired, its status will automatically be set to “Expired”.

first\_call\_resolutions
: *Optional* **[integer](../general/data_types.html)** — The First call resolutions field is used to enter the minimum percentage of [Requests](../requests.html) that are to be completed by the service desk team during their registration.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the first line support agreement.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the first line support agreement.

notice\_date
: *Optional* **[date](../general/data_types.html)** — The Notice date field is used to specify the last day on which the first line support provider organization can still be contacted to terminate the first line support agreement (FLSA) to ensure that it expires on the intended expiry date. The Notice date field is left empty, and the Expiry date field is filled out, when the FLSA is to expire on a specific date and no notice needs to be given to terminate it.

pickup\_target
: *Optional* **[integer](../general/data_types.html)** — The number of minutes within which a new or existing request that has been assigned to the service desk team is assigned to a specific member within the service desk team, is assigned to another team, or is set to a status other than `assigned`.

pickups\_within\_target:
: *Optional* **[integer](../general/data_types.html)** — The minimum percentage of requests that are to be picked up by the service desk team within the pickup target.

provider
: *Required* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)**

rejected\_solutions
: *Optional* **[integer](../general/data_types.html)** — The maximum percentage of requests that were reopened (i.e. which status in the account that is covered by the first line support agreement was updated from `completed` to another status).

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the first line support agreement that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Remarks field.

service\_desk\_team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Service desk team field is used to select the specific [Team](../teams.html) within the first line support provider organization that provides first line support for the users covered by the first line support agreement.

service\_desk\_only\_resolutions
: *Optional* **[integer](../general/data_types.html)** — The minimum percentage of requests that are to be completed by the service desk team without having been assigned to any other team within the account that is covered by the first line support agreement.

service\_desk\_resolutions
: *Optional* **[integer](../general/data_types.html)** — The minimum percentage of requests that are to be completed by the service desk team.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_date
: *Optional* **[date](../general/data_types.html)** — The Start date field is used to specify the first day during which the first line support agreement (FLSA) is active.

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `being_prepared` — The Status field displays the current status of the first line support agreement (FLSA). Valid values are:
: - `being_prepared`: Being Prepared
 - `scheduled_for_activation`: Scheduled for Activation
 - `active`: Active
 - `expired`: Expired

support\_chat\_pickup\_target
: *Optional* **[integer](../general/data_types.html)** — The number of minutes within which a new or existing chat request that has been assigned to the service desk team is assigned to a specific member within the service desk team, is assigned to another team, or is set to a status other than `assigned`.

support\_hours
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Support hours field is used to select a [Calendar](../calendars/index.html) that defines the support hours during which the service desk team can be contacted for first line support.

target\_details
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Target details field is used to provide a description of all the targets of the first line support agreement.

target\_details\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Target details field.

time\_zone
: *Optional* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the start, notice and expiry dates, and to the support hours.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the first line support agreement. If the first line support agreement has no updates it contains the `created_at` value.
