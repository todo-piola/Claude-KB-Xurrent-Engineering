# SLA Notification Schemes API

- [List SLA notification schemes](index.html#list-sla-notification-schemes)
- [Get a single SLA notification scheme](index.html#get-a-single-sla-notification-scheme)
- [Create an SLA notification scheme](index.html#create-an-sla-notification-scheme)
- [Update an SLA notification scheme](index.html#update-an-sla-notification-scheme)
- [Fields](index.html#fields)

## List SLA notification schemes

List all SLA notification schemes for an account:

```
GET /sla_notification_schemes
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"name":"Scheme 1","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"name":"Scheme 2","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"}]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of timesheet settings.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/sla_notification_schemes/enabled`: List all enabled SLA notification schemes
- `/sla_notification_schemes/disabled`: List all disabled SLA notification schemes

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of SLA notification schemes:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `disabled` `name` `created_at` `updated_at`

The filters on `source`, `sourceID`, and `name` are not case sensitive.

### Sorting

By default a collection of SLA notification schemes is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single SLA notification scheme

```
GET /sla_notification_schemes/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2016-12-23T05:09:03-06:00","disabled":false,"id":3,"name":"Scheme 1","source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](index.html#fields).

## Create an SLA notification scheme

```
POST /sla_notification_schemes
```

When creating a new SLA notification scheme [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created SLA notification scheme and is similar to the response in [Get a single SLA notification scheme](index.html#get-a-single-sla-notification-scheme)

## Update an SLA notification scheme

```
PATCH /sla_notification_schemes/:id
```

When updating an SLA notification scheme [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated SLA notification scheme and is similar to the response in [Get a single SLA notification scheme](index.html#get-a-single-sla-notification-scheme)

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the SLA notification scheme was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the SLA notification scheme may no longer be related to any more service offerings.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the SLA notification scheme.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the SLA notification scheme.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the SLA notification scheme. If the SLA notification scheme has no updates it contains the `created_at` value.
