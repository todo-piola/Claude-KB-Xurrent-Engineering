# Service Instances API

- [List service instances](index.html#list-service-instances)
- [Get a single service instance](index.html#get-a-single-service-instance)
- [Create a service instance](index.html#create-a-service-instance)
- [Update a service instance](index.html#update-a-service-instance)
- [Fields](index.html#fields)

## List service instances

List all service instances for an account:

```
GET /service_instances
```

### Response

```
status: 200 OK
```

```
[{"name":"Amsterdam Network","created_at":"2016-03-14T03:10:38-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:38-06:00","service":{"name":"Network Connectivity","id":20,"provider":{"name":"Widget Data Center, External IT","id":30}},"support_team":{"name":"Operations","id":11},"id":23,"status":"in_production"},{"name":"AT&T Smart Phone for Widget Data Center, External IT","created_at":"2016-03-14T03:10:39-06:00","sourceID":null,"updated_at":"2016-03-14T03:11:39-06:00","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"support_team":{"name":"End-User Support, Chicago","account":{"name":"Widget North America","id":"wna"},"id":16},"id":133,"status":"in_production"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of service instances.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/service_instances/active`: List all active service instances
- `/service_instances/inactive`: List all inactive service instances

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of service instances:

`id` `sourceID` `name` `status` `service` `support_team` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `status` `service` `support_team` `created_at` `updated_at`

### Sorting

By default a collection of service instances is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `status` `service` `support_team` `created_at` `updated_at`

## Get a single service instance

```
GET /service_instances/:id
```

### Response

```
status: 200 OK
```

```
{"name":"ITRP Production","remarks":null,"created_at":"2016-03-14T03:10:38-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:53-06:00","service":{"name":"IT Resource Planning (ITRP)","account":{"name":"ITRP Institute","id":"itrp"},"id":1,"provider":{"name":"ITRP Institute, Inc.","account":{"name":"ITRP Institute","id":"itrp"},"id":1}},"account":{"name":"ITRP Institute","id":"itrp"},"support_team":{"name":"Service Desk","account":{"name":"ITRP Institute","id":"itrp"},"id":1},"id":1,"status":"in_production","source":null}
```

The response contains [these fields](index.html#fields).

## Create a service instance

```
POST /service_instances
```

When creating a new service instance [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created service instance and is similar to the response in [Get a single service instance](index.html#get-a-single-service-instance)

## Update a service instance

```
PATCH /service_instances/:id
```

When updating a service instance [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated service instance and is similar to the response in [Get a single service instance](index.html#get-a-single-service-instance)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the service instance was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the service instance.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

first\_line\_team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The First line team field is used to select the team that will automatically be selected in the Team field of requests to which the service instance is linked after they have been submitted using Self Service or when they are generated using the [Requests API](../requests.html), [Mail API](../requests/mail.html) or [Events API](../requests/events.html).

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the service instance.

impact
: *Readonly* **[enum](../general/enumerations/index.html)** — The Impact field shows the impact based on the highest impact of the affected SLAs for which the current user has read access. Valid values are:
: - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

maintenance\_window
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Maintenance window field is used to select a [Calendar](../calendars/index.html) that defines the periods in which workflow tasks with an impact related to this service instance may be implemented.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the service instance.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the service instance. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)**

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Remarks field.

service
: *Required* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the [Service](../services.html) which functionality the service instance provides.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `being_prepared` — The Status field is used to select the current status of the service instance. Valid values are:
: - `being_prepared`: Being Prepared
 - `in_production`: In Production
 - `discontinued`: Discontinued

support\_team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Support team field is used to select the team that will, by default, be selected in the Team field of a request when the service instance is manually selected in the Service instance field of the request, or when the service instance is applied from the Service Hierarchy Browser.

time\_zone
: *Optional* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the selected maintenance window.

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the service instance.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the service instance. If the service instance has no updates it contains the `created_at` value.
