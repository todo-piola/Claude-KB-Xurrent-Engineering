# Closure Codes API

- [List closure codes](index.html#list-closure-codes)
- [Get a single closure code](index.html#get-a-single-closure-code)
- [Create a closure code](index.html#create-a-closure-code)
- [Update a closure code](index.html#update-a-closure-code)
- [Fields](index.html#fields)

## List closure codes

List all closure codes for an account:

```
GET /closure_codes
```

### Response

```
status: 200 OK
```

```
[{"id":1,"sourceID":null,"reference":"hardware_issue_resolved","name":"Hardware Issue - Resolved","description":"Hardware issue resolved successfully","position":1,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":2,"sourceID":null,"reference":"hardware_issue_canceled","name":"Hardware Issue - Canceled","description":"Hardware issue request was canceled","position":2,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"reference":"software_issue_duplicate","name":"Software Issue - Duplicate","description":"Duplicate software issue request","position":3,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:04-06:00"}]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of closure codes.

### Collection Fields

By default the following fields will appear in collections of closure codes:

`id` `sourceID` `reference` `name` `description` `position` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `disabled` `reference` `name` `created_at` `updated_at`

The filters on `source`, `sourceID`, `reference` and `name` are not case sensitive.

### Sorting

By default a collection of closure codes is sorted **ascending** by `position`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `reference` `position` `name` `created_at` `updated_at`

## Get a single closure code

```
GET /closure_codes/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2016-12-23T05:09:03-06:00","description":"Hardware issue resolved successfully","disabled":false,"id":1,"information":"This closure code is used when a hardware-related request has been successfully resolved and the issue has been fixed. The request can be closed with this code when:\n\n1. The reported hardware issue has been identified and addressed\n2. The hardware solution has been implemented and tested\n3. The requester has confirmed the hardware resolution is satisfactory","name":"Hardware Issue - Resolved","position":1,"reference":"hardware_issue_resolved","source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](index.html#fields).

## Create a closure code

```
POST /closure_codes
```

When creating a new closure code [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created closure code and is similar to the response in [Get a single closure code](index.html#get-a-single-closure-code)

## Update a closure code

```
PATCH /closure_codes/:id
```

When updating a closure code [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated closure code and is similar to the response in [Get a single closure code](index.html#get-a-single-closure-code)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the closure code was created.

description
: *Optional* **[string](../general/data_types.html) (max 255)** — The Description field is used to enter a very short description of the closure code, for example “Issue resolved successfully”.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the closure code may not be related to any more requests.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the closure code.

information
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Information field is used to add any additional information about the closure code that might prove useful, especially for specialists when they need to decide which closure code to select for a request.

information\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Information field.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the closure code. Ideally the name of a closure code consists of a single word, such as “Resolved”.

position
: *Optional* **[integer](../general/data_types.html)** — The Position field dictates the position that the closure code takes when it is displayed in a sorted list.

reference
: *Readonly* **[string](../general/data_types.html) (max 128)** — The Reference field is automatically set to the Name field value, written in lower case characters and with all spaces replaced by the underscore character. This reference can be used to link the closure code to a request using the Xurrent REST API or the Xurrent Import functionality.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the closure code. If the closure code has no updates it contains the `created_at` value.
