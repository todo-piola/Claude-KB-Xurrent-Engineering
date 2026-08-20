# Project Templates - Project Task Templates API

- [List all project task templates of a project template](index.html#list-all-project-task-templates-of-a-project-template)
- [Add a project task template to a project template](index.html#add-a-project-task-template-to-a-project-template)
- [Update a project task template linked to a project template](index.html#update-a-project-task-template-linked-to-a-project-template)
- [Remove a project task template from a project template](index.html#remove-a-project-task-template-from-a-project-template)
- [Remove all project task templates from a project template](index.html#remove-all-project-task-templates-from-a-project-template)
- [Fields](index.html#fields)

## List all project task templates of a project template

List all [project task templates](../../project_task_templates.html) of a project template with a specific ID.

```
GET /project_templates/:id/task_templates
```

### Response

```
status: 200 OK
```

```
[{"id":79,"phase_name":"Planning","task_template":{"id":692,"subject":"Prepare detailed implementation plan"}},{"id":81,"phase_name":"Planning","task_template":{"id":699,"subject":"Approval from steering committee for project implementation"}},{"id":82,"phase_name":"Implementation","task_template":{"id":807,"subject":"Finalize the plan for the implementation of the project"}},"..."]
```

The response contains [these fields](../../project_task_templates.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/project_templates/:id/task_templates/disabled`: List all disabled project task templates of a project template with a specific ID.
- `/project_templates/:id/task_templates/enabled`: List all enabled project task templates of a project template with a specific ID.

## Add a project task template to a project template

Add a project task template to a project template with a specific ID.

```
POST /project_templates/:id/task_templates/
```

When creating a new project task template relation for a project template [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":127,"phase_name":"Pilot","task_template":{"id":823,"subject":"Go-live"}}
```

## Update a project task template linked to a project template

Update a project task template relation with a specific ID of a project template with a specific ID.

```
PATCH /project_templates/:id/task_templates/:task_template_aggregate_id
```

When updating an existing project task template relation for a project template [these fields](index.html#fields) are available.

Important:
The `:task_template_aggregate_id` is the ID of the record that links the project task template to the project template. This aggregated record contains the ID of the project task template and the name of the project phase. The ID of the aggregated record can be found using: `GET /project_templates/:id/task_templates`.

### Response

```
status: 200 OK
```

```
{"id":127,"phase_name":"Implementation","task_template":{"id":823,"subject":"Go-live"}}
```

## Remove a project task template from a project template

Remove the relation between a project template with a specific ID and a project task template with a specific ID.

```
DELETE /project_templates/:id/task_templates/:task_template_aggregate_id
```

Important:
The `:task_template_aggregate_id` is the ID of the record that links the project task template to the project template. This aggregated record contains the ID of the project task template and the name of the project phase. The ID of the aggregated record can be found using: `GET /project_templates/:id/task_templates`.

### Response

```
status: 204 No Content
```

## Remove all project task templates from a project template

Remove all links between a project template with a specific ID and its project task templates.

```
DELETE /project_templates/:id/task_templates
```

### Response

```
status: 204 No Content
```

## Fields

id
: *Required* **[integer](../../general/data_types.html)** — The unique ID of the relation between the project template and the project task template.

phase\_name
: *Required* **[string](../../general/data_types.html) (max 50)** — The Phase Name field indicates the phase of the project template that the project task template is a part of.

task\_template
: *Required* **[reference](../../general/data_types.html#references) to [Project Task Template](../../project_task_templates.html)** — The Project Task Template field indicates the project task template that is related to the project template.
