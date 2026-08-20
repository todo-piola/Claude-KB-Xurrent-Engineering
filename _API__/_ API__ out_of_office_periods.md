# Out of Office Periods API

- [List out of office periods](../out_of_office_periods.html#list-out-of-office-periods)
- [Get a single out of office period](../out_of_office_periods.html#get-a-single-out-of-office-period)
- [Create an out of office period](../out_of_office_periods.html#create-an-out-of-office-period)
- [Update an out of office period](../out_of_office_periods.html#update-an-out-of-office-period)
- [Remove an out of office period](../out_of_office_periods.html#remove-an-out-of-office-period)
- [Fields](../out_of_office_periods.html#fields)

## List out of office periods

List all out of office periods for an account:

```
GET /out_of_office_periods
```

### Response

```
status: 200 OK
```

```
[{"id":3,"sourceID":null,"person":{"id":196,"name":"Ellen Brown"},"start_at":"2019-11-18T06:00:00Z","end_at":"2019-11-18T15:45:15Z","created_at":"2019-11-18T08:10:52-06:00","updated_at":"2019-11-18T09:45:16-06:00"},"..."]
```

The response contains [these fields](../out_of_office_periods.html#collection-fields) by default. [Filtering](../out_of_office_periods.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of out of office periods.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/out_of_office_periods/open`: List all out of office periods for which the end time is in the future
- `/out_of_office_periods/completed`: List all out of office periods for which the end time is in the past

### Collection Fields

By default the following [fields](../out_of_office_periods.html#fields) will appear in collections of out of office periods:

`id` `sourceID` `person` `start_at` `end_at` `created_at` `updated_at`

Obtain a different set of [fields](../out_of_office_periods.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../out_of_office_periods.html#fields):

`id` `source` `sourceID` `person` `start_at` `end_at` `created_at` `updated_at`

### Sorting

By default a collection of out of office periods is sorted **ascending** by `start_at`.

The following [fields](../out_of_office_periods.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `person_id` `start_at` `end_at` `created_at` `updated_at`

## Get a single out of office period

```
GET /out_of_office_periods/:id
```

### Response

```
status: 200 OK
```

```
{"approval_delegate":null,"created_at":"2019-11-18T08:10:52-06:00","end_at":"2019-11-18T15:45:15Z","id":3,"person":{"id":196,"name":"Ellen Brown"},"reason":"Time Off - Vacation","source":"4me","sourceID":null,"start_at":"2019-11-18T06:00:00Z","time_allocation":{"id":2,"group":"Time Off","name":"Vacation","account":{"id":"wdc","name":"Widget Data Center"},"localized_name":"Vacation"},"updated_at":"2019-11-18T09:45:16-06:00"}
```

The response contains [these fields](../out_of_office_periods.html#fields).

## Create an out of office period

```
POST /out_of_office_periods
```

When creating a new out of office period [these fields](../out_of_office_periods.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](../out_of_office_periods.html#fields) of the created out of office period and is similar to the response in [Get a single out of office period](../out_of_office_periods.html#get-a-single-out-of-office-period)

## Update an out of office period

```
PATCH /out_of_office_periods/:id
```

When updating an out of office period [these fields](../out_of_office_periods.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](../out_of_office_periods.html#fields) of the updated out of office period and is similar to the response in [Get a single out of office period](../out_of_office_periods.html#get-a-single-out-of-office-period)

## Remove an out of office period

Remove an out of office period with a specific ID.

```
DELETE /out_of_office_periods/:id
```

### Response

```
status: 204 No Content
```

## Fields

approval\_delegate
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The person who is selected as the approval delegate for the out of office period.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the out of office period was created.

end\_at
: *Required* **[datetime](../general/data_types.html)**

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the out of office period.

person
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The person who is out of office.

reason
: *Optional* **[string](../general/data_types.html) (max 80)** — The Reason field is used to enter the reason of the out of office period. Required when the description category of the time allocation is required.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_at
: *Required* **[datetime](../general/data_types.html)**

time\_allocation
: *Optional* **[reference](../general/data_types.html#references) to [Time Allocation](../time_allocations/index.html)** — The time allocation field is used to generate time entries for the out of office period. Only the time allocations without service and customer that are linked to the person’s organization can be selected. This field is required if at least one time allocation exists that meets those conditions.

effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The Effort class field is used to generate time entries for the out of office period. This field is applicable if the timesheet settings linked to the person’s organization has one or more effort classes.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the out of office period. If the out of office period has no updates it contains the `created_at` value.
