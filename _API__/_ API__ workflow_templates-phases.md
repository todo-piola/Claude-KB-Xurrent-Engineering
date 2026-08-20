# Workflow Templates - Phases API

- [List all phases of a workflow template](../phases.html#list-all-phases-of-a-workflow-template)
- [Get a single phase of a workflow template](../phases.html#get-a-single-phase-of-a-workflow-template)
- [Add a phase to a workflow template](../phases.html#add-a-phase-to-a-workflow-template)
- [Update a phase of a workflow template](../phases.html#update-a-phase-of-a-workflow-template)
- [Remove a phase from a workflow template](../phases.html#remove-a-phase-from-a-workflow-template)
- [Remove all phases from a workflow template](../phases.html#remove-all-phases-from-a-workflow-template)
- [Fields](../phases.html#fields)

## List all phases of a workflow template

List all of the phases of a workflow template with a specific ID:

```
GET /workflow_templates/:id/phases
```

### Response

```
status: 200 OK
```

```
[{"id":4558,"...":"..."}]
```

The response contains [these fields](../phases.html#fields) by default.

## Get a single phase of a workflow template

```
GET /workflow_templates/:id/phases/:id
```

### Response

```
status: 200 OK
```

```
{"id":4558,"...":"..."}
```

The response contains [these fields](../phases.html#fields).

## Add a phase to a workflow template

Add a phase to a workflow template with a specific ID.

```
POST /workflow_templates/:id/phases
```

When creating a new phase for a workflow template [these fields](../phases.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":4558,"...":"..."}
```

## Update a phase of a workflow template

Update a phase with a specific ID of a workflow template with a specific ID.

```
PATCH /workflow_templates/:id/phases/:phase_id
```

When updating an existing phase for a workflow template [these fields](../phases.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":4558,"...":"..."}
```

## Remove a phase from a workflow template

Remove a phase with a specific ID from a workflow template with a specific ID.

```
DELETE /workflow_templates/:id/phases/:phase_id
```

### Response

```
status: 204 No Content
```

## Remove all phases from a workflow template

Remove all phases from a workflow template with a specific ID.

```
DELETE /workflow_templates/:id/phases
```

### Response

```
status: 204 No Content
```

## Fields

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the workflow template’s phase was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the workflow template’s phase.

name
: *Required* **[string](../../general/data_types.html) (max 50)** — The Name field is used to enter the name of the workflow template’s phase.

position
: *Optional* **[integer](../../general/data_types.html)** — The Position field dictates the position that the phase takes when it is presented in its workflow template.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the workflow template’s phase. If the phase has no updates it contains the `created_at` value.
