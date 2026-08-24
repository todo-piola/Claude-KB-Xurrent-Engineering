# Project Risk Levels API

- [List project risk levels](index.html#list-project-risk-levels)
- [Get a single project risk level](index.html#get-a-single-project-risk-level)
- [Create a project risk level](index.html#create-a-project-risk-level)
- [Update a project risk level](index.html#update-a-project-risk-level)
- [Fields](index.html#fields)

## List project risk levels

List all project risk levels for an account:

```
GET /project_risk_levels
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"reference":"limited","name":"Limited","description":"Risk of Failure is Limited","position":1,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"reference":"moderate","name":"Moderate","description":"Risk of Failure is Moderate","position":2,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":4,"sourceID":null,"reference":"significant","name":"Significant","description":"Risk of Failure is Significant","position":3,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:04-06:00"}]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of project risk levels.

### Collection Fields

By default the following fields will appear in collections of project risk levels:

`id` `sourceID` `reference` `name` `description` `position` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `disabled` `reference` `name` `created_at` `updated_at`

The filters on `source`, `sourceID`, `reference` and `name` are not case sensitive.

### Sorting

By default a collection of project risk levels is sorted **ascending** by `id`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `reference` `name` `position` `created_at` `updated_at`

## Get a single project risk level

```
GET /project_risk_levels/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2016-12-23T05:09:03-06:00","description":"Risk of Failure is Limited","disabled":false,"id":2,"information":"A project is considered to have limited risk when:\n\n1. The necessary internal resources are readily available for anticipated timeframe\n2. The impact on customers, employees and suppliers is minimal\n3. The success does not rely on technology that has not yet been proven within the Widget organization","name":"Limited","position":1,"reference":"limited","source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](index.html#fields).

## Create a project risk level

```
POST /project_risk_levels
```

When creating a new project risk level [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created project risk level and is similar to the response in [Get a single project risk level](index.html#get-a-single-project-risk-level)

## Update a project risk level

```
PATCH /project_risk_levels/:id
```

When updating a project risk level [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated project risk level and is similar to the response in [Get a single project risk level](index.html#get-a-single-project-risk-level)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the project risk level was created.

description
: *Optional* **[string](../general/data_types.html) (max 255)** — The Description field is used to enter a very short description of the project risk level, for example “Risk of Failure is Significant”.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the project risk level may not be related to any more projects.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the project risk level.

information
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Information field is used to add any additional information about the project risk level that might prove useful, especially for project managers when they need to decide which project risk level to select for a project.

information\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Information field.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the project risk level. Ideally the name of a project risk level consists of a single word, such as “Significant”.

position
: *Optional* **[integer](../general/data_types.html)** — The Position field dictates the position that the project risk level takes when it is displayed in a sorted list.

reference
: *Readonly* **[string](../general/data_types.html) (max 128)** — The Reference field is automatically set to the Name field value, written in lower case characters and with all spaces replaced by the underscore character. This reference can be used to link the project risk level to a project using the Xurrent REST API or the Xurrent Import functionality.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the project risk level. If the project risk level has no updates it contains the `created_at` value.
