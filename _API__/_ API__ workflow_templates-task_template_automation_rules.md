# Workflow Templates - Automation Rules API

## List automation rules of task templates of a workflow template

List all [automation rules](../../automation_rules.html) linked to a task template of the workflow template with a specific ID.

```
GET /workflow_templates/:id/task_template_automation_rules
```

### Response

```
status: 200 OK
```

```
[{"id":21,"disabled":false,"name":"Cancel task for new telephone","trigger":"on status update","position":2,"created_at":"2020-02-15T05:08:46-06:00","updated_at":"2020-02-15T05:08:46-06:00"},{"id":20,"disabled":false,"name":"Add email address to AD task","trigger":"on status update","position":1,"created_at":"2020-02-15T05:08:46-06:00","updated_at":"2020-02-15T05:08:46-06:00"}]
```

The response contains [these fields](../../automation_rules.html#collection-fields) by default.
