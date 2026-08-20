# Sprints API

- [List sprints](index.html#list-sprints)
- [Get a single sprint](index.html#get-a-single-sprint)
- [Create a sprint](index.html#create-a-sprint)
- [Update a sprint](index.html#update-a-sprint)
- [Fields](index.html#fields)

## List sprints

List all sprints for an account:

```
GET /sprints
```

### Response

```
status: 200 OK
```

```
[{"id":565,"sourceID":null,"number":1,"created_at":"2022-08-29T06:00:00-05:00","updated_at":"2022-09-12T04:00:00-05:00","status":"completed","start_at":"2022-08-29T11:00:00Z","scrum_workspace":{"id":1,"name":"Application Development","nodeID":"..."},"nodeID":"..."},{"id":566,"sourceID":null,"number":2,"created_at":"2022-09-12T04:15:00-05:00","updated_at":"2022-09-29T01:50:22-05:00","status":"active","start_at":"2022-09-12T09:15:00Z","scrum_workspace":{"id":1,"name":"Application Development","nodeID":"..."},"nodeID":"..."},{"id":567,"sourceID":null,"number":3,"created_at":"2022-09-29T01:50:22-05:00","updated_at":"2022-09-29T01:50:22-05:00","status":"registered","start_at":"2022-09-26T09:15:00Z","scrum_workspace":{"id":1,"name":"Application Development","nodeID":"..."},"nodeID":"..."},{"id":568,"sourceID":null,"number":1,"created_at":"2022-10-06T03:31:10-05:00","updated_at":"2022-10-06T03:31:10-05:00","status":"registered","start_at":null,"scrum_workspace":{"id":2,"name":"Heavy Iron","nodeID":"..."},"nodeID":"..."}]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of sprints.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of sprints:

`id` `sourceID` `number` `created_at` `updated_at` `status` `start_at` `scrum_workspace`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `created_at` `updated_at` `status` `scrum_workspace`

### Sorting

By default a collection of sprints is sorted **ascending** by `created_at`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `number` `created_at` `updated_at` `start_at`

## Get a single sprint

```
GET /sprints/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2022-10-06T03:31:10-05:00","description":null,"end_at":null,"id":568,"number":1,"scrum_workspace":{"id":2,"name":"Heavy Iron","nodeID":"..."},"source":null,"sourceID":null,"start_at":null,"status":"registered","updated_at":"2022-10-06T03:31:10-05:00","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Create a sprint

```
POST /sprints
```

When creating a new sprint [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created sprint and is similar to the response in [Get a single sprint](index.html#get-a-single-sprint)

## Update a sprint

```
PATCH /sprints/:id
```

When updating a sprint [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated sprint and is similar to the response in [Get a single sprint](index.html#get-a-single-sprint)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the sprint was created.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The description of this sprint (e.g. goal of this sprint).

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

end\_at
: *Optional* **[datetime](../general/data_types.html)** — The date and time the sprint ended, or will end.

name
: *Optional* **[string](../general/data_types.html) (max 128)** - The name of the sprint.

number
: *Required* **[integer](../general/data_types.html)** — Sequence number of this sprint.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the sprint.

scrum\_workspace
: *Readonly* **[reference](../general/data_types.html#references) to [Scrum Workspace](../scrum_workspaces/index.html)** — Scrum workspace this sprint belongs to.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_at
: *Optional* **[datetime](../general/data_types.html)** — The date and time the sprint started, or will start.

status
: *Readonly* **[enum](../general/enumerations/index.html)**, — The current status of the sprint. Valid values are:
: - `registered`: Registered
 - `active`: Active
 - `completed`: Completed

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the sprint. If the sprint has no updates it contains the `created_at` value.
