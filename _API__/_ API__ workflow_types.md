# Workflow Types API

- [List workflow types](../workflow_types.html#list-workflow-types)
- [Get a single workflow type](../workflow_types.html#get-a-single-workflow-type)
- [Create a workflow type](../workflow_types.html#create-a-workflow-type)
- [Update a workflow type](../workflow_types.html#update-a-workflow-type)
- [Fields](../workflow_types.html#fields)

## List Workflow Types

List all workflow types for an account:

```
GET /workflow_types
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"reference":"application_change","name":"Application Change","description":"","position":1,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"reference":"infrastructure_change","name":"Infrastructure Change","description":"","position":2,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"}]
```

The response contains [these fields](../workflow_types.html#collection-fields) by default. [Filtering](../workflow_types.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of workflow types.

### Collection Fields

By default the following fields will appear in collections of workflow types:

`id` `sourceID` `reference` `name` `description` `position` `created_at` `updated_at`

Obtain a different set of [fields](../workflow_types.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../workflow_types.html#fields):

`id` `sourceID` `reference` `name` `disabled` `created_at` `updated_at`

The filters on `sourceID`, `reference` and `name` are not case sensitive.

### Sorting

By default a collection of workflow types is sorted **ascending** by `id`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `reference` `name` `position` `created_at` `updated_at`

## Get a single workflow type

```
GET /workflow_types/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2016-12-23T05:09:03-06:00","description":"","disabled":false,"id":2,"information":"Default workflow type for application changes","name":"Application Change","position":1,"reference":"application_change","source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](../workflow_types.html#fields).

## Create a workflow type

```
POST /workflow_types
```

When creating a new workflow type [these fields](../workflow_types.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](../workflow_types.html#fields) of the created workflow type and is similar to the response in [Get a single workflow type](../workflow_types.html#get-a-single-workflow-type)

## Update a workflow type

```
PATCH /workflow_types/:id
```

When updating a workflow type [these fields](../workflow_types.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](../workflow_types.html#fields) of the updated workflow type and is similar to the response in [Get a single workflow type](../workflow_types.html#get-a-single-workflow-type)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the workflow type was created.

description
: *Optional* **[string](../general/data_types.html) (max 255)** — The Description field is used to enter a very short description of the workflow type, for example “More than 200 workdays or $200K”.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the workflow type may not be related to any more workflows.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the workflow type.

information
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Information field is used to add any additional information about the workflow type that might prove useful, especially for workflow managers when they need to decide which workflow type to select for a workflow.

information\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Information field.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the workflow type. Ideally the name of a workflow type consists of a single word, such as “Large”.

position
: *Optional* **[integer](../general/data_types.html)** — The Position field dictates the position that the workflow type takes when it is displayed in a sorted list.

reference
: *Readonly* **[string](../general/data_types.html) (max 128)** — The Reference field is automatically set to the Name field value, written in lower case characters and with all spaces replaced by the underscore character. This reference can be used to link the workflow type to a workflow using the Xurrent REST API or the Xurrent Import functionality.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the workflow type. If the workflow type has no updates it contains the `created_at` value.
