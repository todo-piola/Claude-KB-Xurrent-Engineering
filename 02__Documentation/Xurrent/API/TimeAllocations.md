# Time Allocations API

- [List time allocations](index.html#list-time-allocations)
- [Get a single time allocation](index.html#get-a-single-time-allocation)
- [Create a time allocation](index.html#create-a-time-allocation)
- [Update a time allocation](index.html#update-a-time-allocation)
- [Fields](index.html#fields)

## List time allocations

List all time allocations for an account:

```
GET /time_allocations
```

### Response

```
status: 200 OK
```

```
[{"id":4,"sourceID":null,"name":"Transparency of Performance (TOP)","group":"Project","created_at":"2016-03-22T21:03:35-05:00","updated_at":"2016-03-22T21:03:35-05:00","localized_group":"Project","localized_name":"Transparency of Performance (TOP)"},{"id":12,"sourceID":null,"name":"Warehouse Ordering (WHO)","group":"Project","created_at":"2016-03-22T21:03:36-05:00","updated_at":"2016-03-22T21:03:36-05:00","disabled":true,"localized_group":"Project","localized_name":"Warehouse Ordering (WHO)"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of time allocations.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/time_allocations/enabled`: List all enabled time allocations
- `/time_allocations/disabled`: List all disabled time allocations

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of time allocations:

`id` `sourceID` `name` `localized_name` `group` `localized_group` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `created_at` `updated_at` `disabled`

### Sorting

By default a collection of time allocations is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single time allocation

```
GET /time_allocations/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2016-03-22T21:03:35-05:00","disabled":false,"customer_category":"selected","effort_class":null,"group":"Project","description_category":"required","id":4,"name":"Transparency of Performance (TOP)","service_category":"selected","source":null,"sourceID":null,"updated_at":"2016-03-22T21:03:35-05:00","localized_group":"Project","localized_name":"Transparency of Performance (TOP)"}
```

The response contains [these fields](index.html#fields).

## Create a time allocation

```
POST /time_allocations
```

When creating a new time allocation [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"coverage":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created time allocation and is similar to the response in [Get a single time allocation](index.html#get-a-single-time-allocation)

## Update a time allocation

```
PATCH /time_allocations/:id
```

When updating a time allocation [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated time allocation and is similar to the response in [Get a single time allocation](index.html#get-a-single-time-allocation)

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the time allocation was created.

customer\_category
: *Required* **[enum](../general/data_types.html)**, default: `none` — The Customer field is used to specify if a [Person](../people.html) who spent on the time allocation needs to select a [Customer Organization](../organizations.html), and if this is the case, whether this person may only select from the customer organizations linked to the time allocation or is allowed to select any customer organization. Valid values are:
: - `none`: None
 - `selected`: One of the Following
 - `any`: Any

description\_category
: *Required* **[enum](../general/data_types.html)**, default: `none` — The Description field is used to specify whether the Description field should be available, and if so, whether it should be required, in the time entries to which the time allocation is related.
 Valid values are:
: - `hidden`: Hidden
 - `optional`: Optional
 - `required`: Required

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the time allocation may no longer be related to any more organizations.

effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The effort class that is selected by default, when someone registers time on this time allocation.

group
: *Optional* **[string](../general/data_types.html) (max 255)** — The Group field is used to include the time allocation in a group.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the time allocation.

localized\_group
: *Readonly* **[string](../general/data_types.html) (max 255)** — Translated Group in the current [language](../index.html#internationalization), defaults to `group` in case no translation is provided.

localized\_name
: *Readonly* **[string](../general/data_types.html) (max 255)** — Translated Name in the current [language](../index.html#internationalization), defaults to `name` in case no translation is provided.

name
: *Required* **[string](../general/data_types.html) (max 160)** — The Name field is used to enter the name of the time allocation.

service\_category
: *Required* **[enum](../general/data_types.html)**, default: `none` — The Service field is used to specify if a Person who spent on the time allocation needs to select a [Service](../services.html), and if this is the case, whether this person may only select from the services linked to the time allocation or is allowed to select any service. Valid values are:
: - `none`: None
 - `selected`: One of the Following
 - `any`: Any

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the time allocation. If the time allocation has no updates it contains the `created_at` value.
