# Project Templates - Phases API

- [List all phases of a project template](index.html#list-all-phases-of-a-project-template)
- [Add a phase to a project template](index.html#add-a-phase-to-a-project-template)
- [Update a phase of a project template](index.html#update-a-phase-of-a-project-template)
- [Remove a phase from a project template](index.html#remove-a-phase-from-a-project-template)
- [Remove all phases from a project template](index.html#remove-all-phases-from-a-project-template)
- [Fields](index.html#fields)

## List all phases of a project template

List all phases of a project template with a specific ID:

```
GET /project_templates/:id/phases
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-12-23T05:09:05-06:00","id":13,"name":"Planning","position":1,"updated_at":"2016-12-23T05:09:05-06:00"},{"created_at":"2016-12-23T05:09:05-06:00","id":14,"name":"Implementation","position":2,"updated_at":"2016-12-23T05:09:05-06:00"}]
```

The response contains [these fields](https://developer.xurrent.com/v1/phases/#collection-fields) by default.

## Add a phase to a project template

Add a new phase to a project template.

```
POST /project_template/:id/phases/
```

When creating a new phase [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"2016-12-23T05:09:05-06:00","id":13,"name":"Planning","position":1,"updated_at":"2016-12-23T05:09:05-06:00"}
```

## Update a phase of a project template

```
PATCH /project_template/:id/phases/:id
```

When updating a project template phase [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"2016-12-23T05:09:05-06:00","id":13,"name":"Planning","position":1,"updated_at":"2016-12-23T05:09:05-06:00"}
```

## Remove a phase from a project template

Remove a phase with a specific ID from a project template with a specific ID.

```
DELETE /project_template/:id/phases/:phase_id
```

### Response

```
status: 204 No Content
```

## Remove all phases from a project template

Remove all phases of a project template with a specific ID. Only possible when the project template has no tasks.

```
DELETE /project_templates/:id/phases
```

### Response

```
status: 204 No Content
```

## Fields

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the project template’s phase was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the project template’s phase.

name
: *Required* **[string](../../general/data_types.html) (max 50)** — The Name field is used to enter the name of the project template’s phase.

position
: *Optional* **[integer](../../general/data_types.html)** — The Position field dictates the position that the phase takes when it is presented in its project template.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the project template’s phase. If the phase has no updates it contains the `created_at` value.
