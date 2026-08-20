# Projects - Phases API

- [List all phases of a project](../phases.html#list-all-phases-of-a-project)
- [Add a phase to a project](../phases.html#add-a-phase-to-a-project)
- [Update a phase of a project](../phases.html#update-a-phase-of-a-project)
- [Remove a phase from a project](../phases.html#remove-a-phase-from-a-project)
- [Remove all phases from a project](../phases.html#remove-all-phases-from-a-project)
- [Fields](../phases.html#fields)

## List all phases of a project

List all phases of a project with a specific ID:

```
GET /projects/:id/phases
```

### Response

```
status: 200 OK
```

```
[{"completed_at":null,"created_at":"2016-12-23T05:09:08-06:00","id":22,"name":"Initiation","position":1,"started_at":"2016-12-23T05:09:08-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:08-06:00"},{"completed_at":null,"created_at":"2016-12-23T05:09:08-06:00","id":23,"name":"Planning","position":2,"started_at":null,"status":"registered","updated_at":"2016-12-23T05:09:08-06:00"},"..."]
```

The response contains [these fields](https://developer.xurrent.com/v1/phases/#collection-fields) by default.

## Add a phase to a project

Add a new phase to a project.

```
POST /project/:id/phases/
```

When creating a new phase [these fields](../phases.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"completed_at":null,"created_at":"2016-12-23T05:09:08-06:00","id":22,"name":"Initiation","position":1,"started_at":"2016-12-23T05:09:08-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:08-06:00"}
```

## Update a phase of a project

```
PATCH /project/:id/phases/:id
```

When updating a project phase [these fields](../phases.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"completed_at":null,"created_at":"2016-12-23T05:09:08-06:00","id":22,"name":"Initiation","position":1,"started_at":"2016-12-23T05:09:08-06:00","status":"in_progress","updated_at":"2016-12-23T05:09:08-06:00"}
```

## Remove a phase from a project

Remove a phase with a specific ID from a project with a specific ID. Only phases with status `registered` may be deleted.

```
DELETE /project/:id/phases/:phase_id
```

### Response

```
status: 204 No Content
```

## Remove all phases from a project

Remove all phases of a project with a specific ID. Only possible when the project has no tasks.

```
DELETE /project/:id/phases
```

### Response

```
status: 204 No Content
```

## Fields

completed\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the project phase was set to the status “Completed”.

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the project phase was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the project phase.

name
: *Required* **[string](../../general/data_types.html) (max 50)** — The Name field is used to enter the name of the project phase.

position
: *Optional* **[integer](../../general/data_types.html)** — The Position field dictates the position that the project phase takes when it is presented in the project’s Gantt chart.

started\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The Started field indicates the date and time at which the first project task of the phase was set to a status other than ‘Registered’ or ‘Canceled’.

status
: *Readonly* **[enum](../../general/enumerations/index.html)**, default: `registered` — The Status field indicates the current status of the project phase. Valid values are:
: - `registered`: Registered
 - `in_progress`: In Progress
 - `completed`: Completed

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the project phase. If the phase has no updates it contains the `created_at` value.
