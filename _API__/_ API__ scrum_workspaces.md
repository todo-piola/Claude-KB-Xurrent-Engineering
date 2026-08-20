# Scrum Workspaces API

- [List scrum workspaces](index.html#list-scrum-workspaces)
- [Get a single scrum workspace](index.html#get-a-single-scrum-workspace)
- [Create a scrum workspace](index.html#create-a-scrum-workspace)
- [Update a scrum workspace](index.html#update-a-scrum-workspace)
- [Fields](index.html#fields)

## List scrum workspaces

List all scrum workspaces for an account:

```
GET /scrum_workspaces
```

### Response

```
status: 200 OK
```

```
[{"id":1,"sourceID":null,"name":"Application Development","created_at":"2022-09-29T01:50:22-05:00","updated_at":"2022-09-29T01:50:22-05:00","nodeID":"..."},{"id":2,"sourceID":null,"name":"Heavy Iron","created_at":"2022-10-06T03:31:10-05:00","updated_at":"2022-10-06T04:48:03-05:00","nodeID":"..."}]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of scrum workspaces.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/scrum_workspaces/enabled`: List all scrum workspaces that are enabled
- `/scrum_workspaces/disabled`: List all scrum workspaces that are disabled

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of scrum workspaces:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `created_at` `updated_at` `disabled`

### Sorting

By default a collection of scrum workspaces is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single scrum workspace

```
GET /scrum_workspaces/:id
```

### Response

```
status: 200 OK
```

```
{"agile_board":{"id":3,"name":"Test","nodeID":"..."},"attachments":[],"created_at":"2022-10-06T03:31:10-05:00","description":"Accelerating innovation with DevOps on mainframe","disabled":false,"id":2,"name":"Heavy Iron","picture_uri":null,"product_backlog":{"id":2,"name":"Mainframe Backlog","nodeID":"..."},"source":"4me","sourceID":null,"sprint_length":4,"team":{"id":15,"name":"Mainframe","nodeID":"..."},"updated_at":"2022-10-06T04:48:03-05:00","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Create a scrum workspace

```
POST /scrum_workspaces
```

When creating a new scrum workspace [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created scrum workspace and is similar to the response in [Get a single scrum workspace](index.html#get-a-single-scrum-workspace)

## Update a scrum workspace

```
PATCH /scrum_workspaces/:id
```

When updating a scrum workspace [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated scrum workspace and is similar to the response in [Get a single scrum workspace](index.html#get-a-single-scrum-workspace)

## Fields

attachments
: *Readonly* **aggregated Attachments**

agile\_board
: *Required* **[reference](../general/data_types.html#references) to [Agile Board](../agile_boards/index.html)** — Agile board used to track the progress of this workspace’s active sprint.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the scrum workspace was created.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — Additional information about the scrum workspace.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether the scrum workspace is in use.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the scrum workspace.

name
: *Required* **[string](../general/data_types.html) (max 128)** — Name of the scrum workspace.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the scrum workspace. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

product\_backlog
: *Required* **[reference](../general/data_types.html#references) to [Product Backlog](../product_backlogs/index.html)** — Product backlog used when planning sprints.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

sprint\_length
: *Required* **[integer](../general/data_types.html)** — Standard length in weeks of new sprints planned in this scrum workspace.

team
: *Required* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — Team planning their work using this scrum workspace.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the scrum workspace. If the scrum workspace has no updates it contains the `created_at` value.
