# Task Templates - Workflow Templates API

## List all workflow templates of a task template

List the relations with [workflow templates](../../workflow_templates.html) that include the task template with a specific ID.

```
GET /task_templates/:id/workflow_templates
```

### Response

```
status: 200 OK
```

```
[{"id":281,"sourceID":null,"subject":"Non-standard infrastructure change","service":null,"created_at":"2015-12-10T19:18:39-06:00","updated_at":"2015-12-10T19:18:39-06:00"},{"id":704,"sourceID":null,"subject":"Unix software patch or minor upgrade","service":{"id":39,"name":"Unix Server","provider":{"id":44,"name":"Widget Data Center, External IT","account":{"id":"widget","name":"Widget International"}},"localized_name":"Unix Server"},"created_at":"2015-12-10T19:18:39-06:00","updated_at":"2015-12-10T19:18:39-06:00"}]
```

The response contains [these fields](../../workflow_templates.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/task_templates/:id/workflow_templates/disabled`: List all disabled workflow templates of a task template with a specific ID
- `/task_templates/:id/workflow_templates/enabled`: List all enabled workflow templates of a task template with a specific ID
