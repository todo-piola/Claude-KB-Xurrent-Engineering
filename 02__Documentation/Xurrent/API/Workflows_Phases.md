# Workflows - Phases API

- [List all phases of a workflow](../phases.html#list-all-phases-of-a-workflow)
- [Get a single phase of a workflow](../phases.html#get-a-single-phase-of-a-workflow)
- [Add a phase to a workflow](../phases.html#add-a-phase-to-a-workflow)
- [Update a phase of a workflow](../phases.html#update-a-phase-of-a-workflow)
- [Remove a phase from a workflow](../phases.html#remove-a-phase-from-a-workflow)
- [Remove all phases from a workflow](../phases.html#remove-all-phases-from-a-workflow)
- [Fields](../phases.html#fields)

## List all phases of a workflow

List all of the phases of a workflow with a specific ID:

```
GET /workflows/:id/phases
```

### Response

```
status: 200 OK
```

```
[{"id":4558,"...":"..."}]
```

The response contains [these fields](../phases.html#fields) by default.

## Get a single phase of a workflow

```
GET /workflows/:id/phases/:id
```

### Response

```
status: 200 OK
```

```
{"id":4558,"...":"..."}
```

The response contains [these fields](../phases.html#fields).

## Add a phase to a workflow

Add a phase to a workflow with a specific ID.

```
POST /workflows/:id/phases
```

When creating a new phase for a workflow [these fields](../phases.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":4558,"...":"..."}
```

## Update a phase of a workflow

Update a phase with a specific ID of a workflow with a specific ID.

```
PATCH /workflows/:id/phases/:phase_id
```

When updating an existing phase for a workflow [these fields](../phases.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":4558,"...":"..."}
```

## Remove a phase from a workflow

Remove a phase with a specific ID from a workflow with a specific ID.

```
DELETE /workflows/:id/phases/:phase_id
```

### Response

```
status: 204 No Content
```

## Remove all phases from a workflow

Remove all phases from a workflow with a specific ID.

```
DELETE /workflows/:id/phases
```

### Response

```
status: 204 No Content
```

## Fields

completed\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the workflow phase was set to the status “Completed”.

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the workflow phase was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the workflow phase.

name
: *Required* **[string](../../general/data_types.html) (max 50)** — The Name field is used to enter the name of the workflow phase.

position
: *Optional* **[integer](../../general/data_types.html)** — The Position field dictates the position that the workflow phase takes when it is presented in the workflow’s Gantt chart.

started\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The Started field indicates the date and time at which the first workflow task of the phase was set to a status other than ‘Registered’ or ‘Canceled’.

status
: *Readonly* **[enum](../../general/enumerations/index.html)**, default: `registered` — The Status field indicates the current status of the workflow phase. Valid values are:
: - `registered`: Registered
 - `in_progress`: In Progress
 - `completed`: Completed

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the workflow phase. If the phase has no updates it contains the `created_at` value.
