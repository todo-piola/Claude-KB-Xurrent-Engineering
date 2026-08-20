# Waiting for Customer Follow-Ups API

- [List waiting for customer follow-ups](index.html#list-waiting-for-customer-follow-ups)
- [Get a single waiting for customer follow-up](index.html#get-a-single-waiting-for-customer-follow-up)
- [Create a waiting for customer follow-up](index.html#create-a-waiting-for-customer-follow-up)
- [Update a waiting for customer follow-up](index.html#update-a-waiting-for-customer-follow-up)
- [Fields](index.html#fields)

## List waiting for customer follow-ups

List all waiting for customer follow-ups for an account:

```
GET /waiting_for_customer_follow_ups
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

- `/waiting_for_customer_follow_ups/enabled`: List all enabled waiting for customer follow-ups
- `/waiting_for_customer_follow_ups/disabled`: List all disabled waiting for customer follow-ups

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of waiting for customer follow-ups:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `disabled` `name` `created_at` `updated_at`

The filters on `source`, `sourceID`, and `name` are not case sensitive.

### Sorting

By default a collection of waiting for customer follow-ups is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single waiting for customer follow-up

```
GET /waiting_for_customer_follow_ups/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2016-12-23T05:09:03-06:00","disabled":false,"id":3,"name":"Scheme 1","auto_complete":true,"source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](index.html#fields).

## Create a waiting for customer follow-up

```
POST /waiting_for_customer_follow_ups
```

When creating a new waiting for customer follow-up [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created waiting for customer follow-up and is similar to the response in [Get a single waiting for customer follow-up](index.html#get-a-single-waiting-for-customer-follow-up)

## Update a waiting for customer follow-up

```
PATCH /waiting_for_customer_follow_ups/:id
```

When updating a waiting for customer follow-up [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated waiting for customer follow-up and is similar to the response in [Get a single waiting for customer follow-up](index.html#get-a-single-waiting-for-customer-follow-up)

## Fields

auto\_complete
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Auto-complete when the final waiting for customer follow-up notification is sent.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the waiting for customer follow-up was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the waiting for customer follow-up may no longer be related to any more service offerings.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the waiting for customer follow-up.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the waiting for customer follow-up.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the waiting for customer follow-up. If the waiting for customer follow-up has no updates it contains the `created_at` value.
