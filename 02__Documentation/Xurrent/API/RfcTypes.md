# RFC Types API

- [List RFC types](../rfc_types.html#list-rfc-types)
- [Get a single RFC type](../rfc_types.html#get-a-single-rfc-type)
- [Create a RFC type](../rfc_types.html#create-a-rfc-type)
- [Update a RFC type](../rfc_types.html#update-a-rfc-type)
- [Fields](../rfc_types.html#fields)

## List RFC Types

List all RFC types for an account:

```
GET /rfc_types
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"reference":"service_request","name":"Service Request","position":1,"created_at":"2026-02-23T05:09:03-06:00","updated_at":"2026-02-23T05:09:03-06:00"},{"id":3,"sourceID":null,"reference":"non_standard_request","name":"Non Standard Request","position":2,"created_at":"2026-02-23T05:09:03-06:00","updated_at":"2026-02-23T05:09:03-06:00"}]
```

The response contains [these fields](../rfc_types.html#collection-fields) by default. [Filtering](../rfc_types.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of RFC types.

### Collection Fields

By default the following fields will appear in collections of RFC types:

`id` `sourceID` `reference` `name` `position` `created_at` `updated_at`

Obtain a different set of [fields](../rfc_types.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../rfc_types.html#fields):

`id` `sourceID` `reference` `name` `disabled` `created_at` `updated_at`

The filters on `sourceID`, `reference` and `name` are not case sensitive.

### Sorting

By default a collection of RFC types is sorted **ascending** by `id`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `reference` `name` `position` `created_at` `updated_at`

## Get a single RFC type

```
GET /rfc_types/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2026-02-23T05:09:03-06:00","disabled":false,"id":2,"information":"Request for standard service","name":"Service Request","position":1,"reference":"service_request","source":null,"sourceID":null,"updated_at":"2026-02-23T05:09:03-06:00"}
```

The response contains [these fields](../rfc_types.html#fields).

## Create a RFC type

```
POST /rfc_types
```

When creating a new RFC type [these fields](../rfc_types.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](../rfc_types.html#fields) of the created RFC type and is similar to the response in [Get a single RFC type](../rfc_types.html#get-a-single-rfc-type)

## Update a RFC type

```
PATCH /rfc_types/:id
```

When updating a RFC type [these fields](../rfc_types.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](../rfc_types.html#fields) of the updated RFC type and is similar to the response in [Get a single RFC type](../rfc_types.html#get-a-single-rfc-type)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the RFC type was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the RFC type may not be related to any more rfcs.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the RFC type.

information
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Information field is used to add any additional information about the RFC type that might prove useful.

information\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Information field.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the RFC type. Ideally the name of a RFC type consists of a single word, such as “Large”.

position
: *Optional* **[integer](../general/data_types.html)** — The Position field dictates the position that the RFC type takes when it is displayed in a sorted list.

reference
: *Readonly* **[string](../general/data_types.html) (max 128)** — The Reference field is automatically set to the Name field value, written in lower case characters and with all spaces replaced by the underscore character. This reference can be used to link the RFC type to a rfc using the Xurrent REST API or the Xurrent Import functionality.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the RFC type. If the RFC type has no updates it contains the `created_at` value.
