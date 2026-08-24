# Reservations API

- [List reservations](../reservations.html#list-reservations)
- [Get a single reservation](../reservations.html#get-a-single-reservation)
- [Create a reservation](../reservations.html#create-a-reservation)
- [Update a reservation](../reservations.html#update-a-reservation)
- [Fields](../reservations.html#fields)

## List reservations

List all reservations for an account:

```
GET /reservations
```

### Response

```
status: 200 OK
```

```
[{"id":5,"sourceID":null,"name":"Conference Room Reservation","status":"canceled","person_id":92,"start_at":"2020-07-13T14:15:00Z","end_at":"2020-07-13T15:15:00Z","created_at":"2020-07-10T20:28:00-05:00","updated_at":"2020-07-10T20:29:35-05:00","nodeID":"..."},{"id":6,"sourceID":null,"name":"Reserve a pool car","status":"being_prepared","person_id":92,"start_at":"2020-07-13T15:00:00Z","end_at":"2020-07-13T23:00:00Z","created_at":"2020-07-11T18:32:42-05:00","updated_at":"2020-07-13T09:30:59-05:00","nodeID":"..."},"..."]
```

The response contains [these fields](../reservations.html#collection-fields) by default. [Filtering](../reservations.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of reservations.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/reservations/open`: List all reservations that are not ended or canceled
- `/reservations/completed`: List all reservations that are ended or canceled

### Collection Fields

By default the following [fields](../reservations.html#fields) will appear in collections of reservations:

`id` `sourceID` `name` `status` `person` `start_at` `end_at` `created_at` `updated_at`

Obtain a different set of [fields](../reservations.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../reservations.html#fields):

`id` `source` `sourceID` `name` `status` `start_at` `end_at` `created_at` `updated_at`

### Sorting

By default a collection of reservations is sorted **ascending** by `start_at`.

The following [fields](../reservations.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `start_at` `end_at` `created_at` `updated_at`

## Get a single reservation

```
GET /reservations/:id
```

### Response

```
status: 200 OK
```

```
{"ci":{"id":2513,"label":"CAR00024","name":"Ford F150 Pickup Truck","nodeID":"..."},"created_at":"2020-07-11T18:32:42-05:00","end_at":"2020-07-13T23:00:00Z","id":6,"name":"Reserve a pool car","person":{"id":92,"name":"Beatrice Baldwin","account":{"id":"widget","name":"Widget International"},"nodeID":"..."},"preparation_start_at":"2020-07-13T14:30:00Z","request":{"id":80162,"subject":"Reserve a pool car","nodeID":"..."},"reservation_offering":{"id":25,"name":"Pool Car","nodeID":"..."},"source":null,"sourceID":null,"start_at":"2020-07-13T15:00:00Z","status":"being_prepared","updated_at":"2020-07-13T09:30:59-05:00","nodeID":"..."}
```

The response contains [these fields](../reservations.html#fields).

## Create a reservation

```
POST /reservations
```

When creating a new reservation [these fields](../reservations.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](../reservations.html#fields) of the created reservation and is similar to the response in [Get a single reservation](../reservations.html#get-a-single-reservation)

## Update a reservation

```
PATCH /reservations/:id
```

When updating a reservation [these fields](../reservations.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](../reservations.html#fields) of the updated reservation and is similar to the response in [Get a single reservation](../reservations.html#get-a-single-reservation)

## Fields

ci
: *Required* **[reference](../general/data_types.html#references) to [configuration item](../configuration_items/index.html)** — The ID of the related asset.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the reservation was created.

end\_at
: *Required* **[datetime](../general/data_types.html)** — The End field is used to specify the moment at which the reservation ends.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the reservation.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter a name for the reservation.

only\_this\_occurrence
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Set to true when only this occurrence of a recurrent reservation should be updated. Otherwise this and all future occurrences will be updated.

person
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The ID of the person for whom the reservation is made.

preparation\_start\_at
: *Readonly* **[datetime](../general/data_types.html)** — The preparation start field is used to specify the moment at which the reservation is being prepared.

recurrence
: *Optional* **aggregated** — The recurrence settings hash, missing in case the reservation has no recurrency defined. See [Recurrence](../recurrences.html) for the fields in the recurrence hash.

reservation\_offering
: *Optional* **[reference](../general/data_types.html#references) to [Reservation Offering](../reservation_offerings/index.html)** — The ID of the Reservation offering that was related to the request template used to request the reservation.

request
: *Optional* **[reference](../general/data_types.html#references) to [Request](https://developer.xurrent.com/v1/request/)** — The ID of the request used to create the reservation.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_at
: *Required* **[datetime](../general/data_types.html)** — The Start field is used to specify the moment at which the reservation begins.

status
: *Required* **[enum](../general/enumerations/index.html)**, default: `confirmed` — The Status field is used to specify whether a reservation that was requested using the reservation offering is immediately confirmed after it has been submitted, or that an action (such as an approval) is still required before it can be confirmed. Valid values are:
: - `provisional`: The reservation has been provisionally requested.
 - `pending`: The reservation has been requested and is awaiting confirmation.
 - `confirmed`: The reservation is confirmed.
 - `being_prepared`: The configuration item is being prepared before the start of the reservation.
 - `active`: The reservation is currently in progress.
 - `canceled`: The reservation has been canceled.
 - `ended`: The reservation has already ended.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the reservation. If the reservation has no updates it contains the `created_at` value.
