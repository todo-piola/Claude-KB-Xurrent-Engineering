# Effort Classes API

- [List effort classes](../effort_classes.html#list-effort-classes)
- [Get a single effort class](../effort_classes.html#get-a-single-effort-class)
- [Create an effort class](../effort_classes.html#create-an-effort-class)
- [Update an effort class](../effort_classes.html#update-an-effort-class)
- [Fields](../effort_classes.html#fields)

## List effort classes

List all effort classes for an account:

```
GET /effort_classes
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"name":"Standard","position":1,"cost_multiplier":"1.0","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"name":"Overtime","position":2,"cost_multiplier":"1.65","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"}]
```

The response contains [these fields](../effort_classes.html#collection-fields) by default. [Filtering](../effort_classes.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of timesheet settings.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/effort_classes/enabled`: List all enabled effort classes
- `/effort_classes/disabled`: List all disabled effort classes

### Collection Fields

By default the following [fields](../effort_classes.html#fields) will appear in collections of effort classes:

`id` `sourceID` `name` `position` `cost_multiplier` `created_at` `updated_at`

Obtain a different set of [fields](../effort_classes.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../effort_classes.html#fields):

`id` `source` `sourceID` `disabled` `name` `created_at` `updated_at`

The filters on `source`, `sourceID`, and `name` are not case sensitive.

### Sorting

By default a collection of effort classes is sorted **ascending** by `position`.

The following [fields](../effort_classes.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `position` `created_at` `updated_at`

## Get a single effort class

```
GET /effort_classes/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2016-12-23T05:09:03-06:00","disabled":false,"id":3,"name":"Overtime","position":2,"cost_multiplier":"1.65","source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](../effort_classes.html#fields).

## Create an effort class

```
POST /effort_classes
```

When creating a new effort class [these fields](../effort_classes.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../effort_classes.html#fields) of the created effort class and is similar to the response in [Get a single effort class](../effort_classes.html#get-a-single-effort-class)

## Update an effort class

```
PATCH /effort_classes/:id
```

When updating an effort class [these fields](../effort_classes.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../effort_classes.html#fields) of the updated effort class and is similar to the response in [Get a single effort class](../effort_classes.html#get-a-single-effort-class)

## Fields

cost\_multiplier
: *Optional* **[decimal](../general/data_types.html)**, default: `1` — The amount with which to multiply the cost of time entries with this effort class.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the effort class was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the effort class may no longer be related to any more timesheet settings.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the effort class.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the effort class.

position
: *Optional* **[integer](../general/data_types.html)** — The Position field dictates the position that the effort class takes when it is displayed in a sorted list.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the effort class. If the effort class has no updates it contains the `created_at` value.
