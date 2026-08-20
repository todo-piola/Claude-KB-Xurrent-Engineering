# Sprints - Backlog Items API

- [List sprint backlog items](index.html#list-sprint-backlog-items)
- [Get a single sprint backlog item](index.html#get-a-single-sprint-backlog-item)
- [Update a sprint backlog item](index.html#update-a-sprint-backlog-item)
- [Fields](index.html#fields)

## List sprint backlog items

List all sprint backlog items for an account:

```
GET /sprints/:id/sprint_backlog_items
```

### Response

```
status: 200 OK
```

```
[{"id":26,"position":1,"estimate":13,"created_at":"2022-10-06T04:48:56-05:00","updated_at":"2022-10-06T04:48:56-05:00","sprint":{"id":566,"scrum_workspace":{"id":1,"name":"Application Development","nodeID":"..."},"number":2,"nodeID":"..."},"nodeID":"...","request":{"id":70260,"subject":"Add ability to specify variance limits to the Quality Control application","account":{"id":"wna-it","name":"Widget N. America - IT"},"nodeID":"..."}},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../../general/pagination.html) are available to reduce/limit the collection of sprint backlog items.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of sprint backlog items:

`id` `position` `estimate` `sprint` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](index.html#fields):

`created_at` `updated_at`

### Sorting

By default a collection of sprint backlog items is sorted **ascending** by `position`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../../general/ordering.html):

`position` `created_at` `updated_at`

## Get a single sprint backlog item

```
GET /sprints/:id/sprint_backlog_items/:id
```

### Response

```
status: 200 OK
```

```
{"position":1,"estimate":13,"created_at":"2022-10-06T04:48:56-05:00","updated_at":"2022-10-06T04:48:56-05:00","planned":false,"done":false,"nodeID":"...","request":{"id":70260,"subject":"Add ability to specify variance limits to the Quality Control application","account":{"id":"wna-it","name":"Widget N. America - IT"},"nodeID":"..."}}
```

The response contains [these fields](index.html#fields).

## Update a sprint backlog item

```
PATCH /sprints/:id/sprint_backlog_items/:id
```

When updating a sprint backlog item [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated sprint backlog item and is similar to the response in [Get a single sprint backlog item](index.html#get-a-single-sprint-backlog-item)

## Fields

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the sprint backlog item was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the sprint backlog item.

done
: *Readonly* **[boolean](../../general/data_types.html)** — Whether this item has been completed in this sprint. `null` indicates the item was removed from the sprint.

estimate
: *Optional* **[integer](../../general/data_types.html)** — Estimate of the relative size of this record on the sprint backlog.

planned
: *Readonly* **[boolean](../../general/data_types.html)**, default: `false` — Whether this item was part of the sprint backlog when the sprint was started.

position
: *Optional* **[integer](../../general/data_types.html)** — Position of this record on the sprint backlog. The top item has position 1.

problem
: *Readonly* **[reference](../../general/data_types.html#references) to [Problem](../../problems.html)** — The Problem field is filled for problems on the sprint backlog.

project\_task
: *Readonly* **[reference](../../general/data_types.html#references) to [Project Task](../../project_tasks.html)** — The Project Task field is filled for project tasks on the sprint backlog.

request
: *Readonly* **[reference](../../general/data_types.html#references) to [Request](../../requests.html)** — The Request field is filled for requests on the sprint backlog.

sprint
: *Readonly* **[reference](../../general/data_types.html#references) to [Sprint](../index.html)** — The sprint this backlog item is part of.

task
: *Readonly* **[reference](../../general/data_types.html#references) to [Task](../../tasks.html)** — The Task field is filled for tasks on the sprint backlog.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the sprint backlog item. If the sprint backlog item has no updates it contains the `created_at` value.
