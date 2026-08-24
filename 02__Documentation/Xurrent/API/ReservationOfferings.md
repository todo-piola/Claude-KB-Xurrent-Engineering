# Reservation Offerings API

- [List reservation offerings](index.html#list-reservation-offerings)
- [Get a single reservation offering](index.html#get-a-single-reservation-offering)
- [Create a reservation offering](index.html#create-a-reservation-offering)
- [Update a reservation offering](index.html#update-a-reservation-offering)
- [Fields](index.html#fields)

## List reservation offerings

List all reservation offerings for an account:

```
GET /reservation_offerings
```

### Response

```
status: 200 OK
```

```
[{"id":7,"sourceID":null,"name":"4me training environment","created_at":"2020-07-09T20:34:33-05:00","updated_at":"2020-07-09T20:34:51-05:00","nodeID":"..."},{"id":24,"sourceID":null,"name":"Conference Rooms","created_at":"2020-07-10T20:24:05-05:00","updated_at":"2020-07-13T04:19:48-05:00","nodeID":"..."},{"id":25,"sourceID":null,"name":"Pool Car","created_at":"2020-07-11T17:38:13-05:00","updated_at":"2020-07-11T18:17:53-05:00","nodeID":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of reservation offerings.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/reservation_offerings/disabled`: List all disabled reservation offerings
- `/reservation_offerings/enabled`: List all enabled reservation offerings

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of reservation offerings:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `disabled` `created_at` `updated_at`

### Sorting

By default a collection of reservation offerings is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

### Response

The response is similar to the response in [List reservation offerings](index.html#list-reservation-offerings)

## Get a single reservation offering

```
GET /reservation_offerings/:id
```

### Response

```
status: 200 OK
```

```
{"calendar":{"id":50,"name":"24x7 (Monday through Sunday)","nodeID":"..."},"created_at":"2020-07-09T20:34:33-05:00","disabled":false,"filters":[],"id":7,"initial_status":"confirmed","max_advance_duration":null,"max_duration":10080,"min_advance_duration":null,"min_duration":240,"multi_day":true,"name":"4me training environment","preparation_duration":null,"service_instance":{"id":77,"name":"Service Management (Xurrent) Production","localized_name":"Service Management (Xurrent) Production","nodeID":"..."},"source":null,"sourceID":null,"step_duration":240,"time_zone":"Central Time (US & Canada)","updated_at":"2020-07-09T20:34:51-05:00","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Create a reservation offering

```
POST /reservation_offerings
```

When creating a new reservation offering [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"brand":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created reservation offering and is similar to the response in [Get a single reservation offering](index.html#get-a-single-reservation-offering)

## Update a reservation offering

```
PATCH /reservation_offerings/:id
```

When updating a reservation offering [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"brand":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated reservation offering and is similar to the response in [Get a single reservation offering](index.html#get-a-single-reservation-offering)

## Fields

allow\_repeat
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether it is allowed to create recurrent reservations for this offering.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the reservation offering may not be related to a request template any more.

calendar
: *Required* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Calendar field is used to select the [Calendar](../calendars/index.html) that defines the hours during which the [Configuration Items](../configuration_items/index.html) can be made available for temporary use.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the reservation offering was created.

filters
: *Optional* **array of [strings](../general/data_types.html)** — The Filters field allows filters to be selected that people, who are selecting a configuration item of the reservation offering, can use to limit the list of configuration items to only those that meet specific criteria, such as the configuration item’s product or site.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the reservation offering.

initial\_status
: *Required* **[enum](../general/enumerations/index.html)** — The Initial status field is used to specify whether a reservation that was requested using the reservation offering is immediately confirmed after it has been submitted, or that an action (such as an approval) is still required before it can be confirmed. Valid values are:
: - `pending`: The requested reservation is awaiting confirmation.
 - `confirmed`: The requested reservation is confirmed.

max\_advance\_duration
: *Optional* **[integer](../general/data_types.html)** — The Max. advance duration field is used to specify how far in the future the start of a reservation is allowed to be scheduled using the reservation offering.

max\_duration
: *Required* **[integer](../general/data_types.html)** — The Max. duration field is used to specify the maximum length of time for which a configuration item of the reservation offering can be reserved.

min\_advance\_duration
: *Optional* **[integer](../general/data_types.html)** — The Min. advance duration field is used to specify how much advance notice is needed from the moment a reservation is requested using the reservation offering and the start of the reservation. This is typically the time needed to prepare a configuration item of the reservation offering.

min\_duration
: *Required* **[integer](../general/data_types.html)** — The Min. duration field is used to specify the minimum length of time for which a configuration item of the reservation offering can be reserved.

multi\_day
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Multi-day box is checked when a reservation request that uses the reservation offering is allowed to start on one day and end on another. When `true` the duration of a reservation that makes use of the reservation offering is defined by filling out the End field instead of the duration field.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter a name for the reservation offering.

preparation\_duration
: *Optional* **[integer](../general/data_types.html)** — The Preparation duration field is used to specify the amount of time needed to prepare a configuration item of the reservation offering for the next person who reserved it. People are not be able to request a reservation of a configuration item if it overlaps with the preparation duration of an existing reservation for the same configuration item.

service\_instance
: *Required* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The service instance field is used to select the [Service Instance](../service_instances/index.html) for which people need to be covered in order to be able to make use of the reservation offering.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

step\_duration
: *Required* **[integer](../general/data_types.html)** — The Step duration field is used specify the time increments for the duration of a reservation that is requested using the reservation offering.

time\_zone
: *Required* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the selected calendar.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the team. If the team has no updates it contains the `created_at` value.
