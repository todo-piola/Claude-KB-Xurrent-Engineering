# Risk Severities API

- [List risk severities](index.html#list-risk-severitys)
- [Get a single risk severity](index.html#get-a-single-risk-severity)
- [Create a risk severity](index.html#create-a-risk-severity)
- [Update a risk severity](index.html#update-a-risk-severity)
- [Fields](index.html#fields)

## List risk severities

List all risk severities for an account:

```
GET /risk_severities
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"reference":"low","name":"Low","description":"Risk is Limited","position":1,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of risk severities.

### Collection Fields

By default the following fields will appear in collections of risk severities:

`id` `sourceID` `reference` `name` `description` `position` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `disabled` `reference` `name` `created_at` `updated_at` `disabled`

The filters on `source`, `sourceID`, `reference` and `name` are not case sensitive.

### Sorting

By default a collection of risk severities is sorted **ascending** by `id`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `reference` `name` `position` `created_at` `updated_at`

## Get a single risk severity

```
GET /risk_severities/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2016-12-23T05:09:03-06:00","description":"Risk is Limited","disabled":false,"id":2,"information":"A risk is considered to be low when: ...","name":"Low","position":1,"reference":"low","source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](index.html#fields).

## Create a risk severity

```
POST /risk_severities
```

When creating a new risk severity [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created risk severity and is similar to the response in [Get a single risk severity](index.html#get-a-single-risk-severity).

## Update a risk severity

```
PATCH /risk_severities/:id
```

When updating a risk severity [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated risk severity and is similar to the response in [Get a single risk severity](index.html#get-a-single-risk-severity).

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the risk severity was created.

description
: *Optional* **[string](../general/data_types.html) (max 255)** — The Description field is used to enter a very short description of the risk severity, for example “Risk is Significant”.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the risk severity may not be related to any more risks.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the risk severity.

information
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Information field is used to add any additional information about the risk severity that might prove useful, especially for risk managers when they need to decide which severity to select for a risk.

information\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Information field.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the risk severity. Ideally the name of a risk severity consists of a single word, such as “High”.

position
: *Optional* **[integer](../general/data_types.html)** — The Position field dictates the position that the risk severity takes when it is displayed in a sorted list.

reference
: *Readonly* **[string](../general/data_types.html) (max 128)** — The Reference field is automatically set to the Name field value, written in lower case characters and with all spaces replaced by the underscore character. This reference can be used to link the risk severity to a risk using the Xurrent REST API or the Xurrent Import functionality.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the risk severity. If the risk severity has no updates it contains the `created_at` value.
