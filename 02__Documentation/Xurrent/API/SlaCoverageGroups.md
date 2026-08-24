# SLA Coverage Groups API

- [List SLA coverage groups](index.html#list-sla-coverage-groups)
- [Get a single SLA coverage group](index.html#get-a-single-sla-coverage-group)
- [Create a SLA coverage group](index.html#create-a-sla-coverage-group)
- [Update a SLA coverage group](index.html#update-a-sla-coverage-group)
- [Fields](index.html#fields)

## List SLA coverage groups

List all SLA coverage groups for an account:

```
GET /sla_coverage_groups
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2023-11-17T02:37:24-06:00","description":null,"disabled":false,"id":2,"name":"Beatrice","search_phrase":null,"source":"4me","sourceID":null,"updated_at":"2023-11-17T02:37:24-06:00","nodeID":"..."},{"created_at":"2023-11-17T02:41:10-06:00","description":null,"disabled":false,"id":3,"name":"Finance","search_phrase":"Finance","source":"4me","sourceID":null,"updated_at":"2023-11-17T02:41:10-06:00","nodeID":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of SLA coverage groups.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/sla_coverage_groups/enabled`: List all SLA coverage groups that are enabled
- `/sla_coverage_groups/disabled`: List all SLA coverage groups that are disabled

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of SLA coverage groups:

`id` `sourceID` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `created_at` `updated_at`

### Sorting

By default a collection of SLA coverage groups is sorted **ascending** by `created_at`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `created_at` `updated_at`

## Get a single SLA coverage group

```
GET /sla_coverage_groups/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2023-11-17T02:37:24-06:00","description":null,"disabled":false,"id":2,"name":"Beatrice","search_phrase":null,"source":"4me","sourceID":null,"updated_at":"2023-11-17T02:37:24-06:00","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Create a SLA coverage group

```
POST /sla_coverage_groups
```

When creating a new SLA coverage group [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created SLA coverage group and is similar to the response in [Get a single SLA coverage group](index.html#get-a-single-sla-coverage-group)

## Update a SLA coverage group

```
PATCH /sla_coverage_groups/:id
```

When updating a SLA coverage group [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated SLA coverage group and is similar to the response in [Get a single SLA coverage group](index.html#get-a-single-sla-coverage-group)

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the SLA coverage group was created.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to add any additional information about the SLA coverage group that might prove useful.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Description field.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the SLA coverage group.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the SLA coverage group.

search\_phrase
: *Optional* **[string](../general/data_types.html) (max 255)** - The search phrase used to filter the people.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the SLA coverage group. If the SLA coverage group has no updates it contains the `created_at` value.
