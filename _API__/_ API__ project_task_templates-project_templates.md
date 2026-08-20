# Project Task Templates - Project Templates API

## List all project templates of a project task template

List the relations with [project templates](../../project_templates/index.html) that include the project task template with a specific ID.

```
GET /project_task_templates/:id/project_templates
```

### Response

```
status: 200 OK
```

```
[{"id":456,"sourceID":null,"subject":"Large project phases","created_at":"2016-12-23T05:09:05-06:00","updated_at":"2016-12-23T05:09:05-06:00"},{"id":448,"sourceID":null,"subject":"Medium project phases","created_at":"2016-12-23T05:09:05-06:00","updated_at":"2016-12-23T05:09:05-06:00"},"..."]
```

The response contains [these fields](../../project_templates/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/project_task_templates/:id/project_templates/disabled`: List all disabled Workflow Templates of a Task Template with a specific ID
- `/project_task_templates/:id/project_templates/enabled`: List all enabled Workflow Templates of a Task Template with a specific ID
