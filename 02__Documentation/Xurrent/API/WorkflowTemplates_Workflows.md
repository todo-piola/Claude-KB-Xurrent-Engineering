# Workflow Templates - Workflows API

## List workflows of a workflow template

List all [workflows](../../workflows.html) that were created using the workflow template with a specific ID.

```
GET /workflow_templates/:id/workflows
```

### Response

```
status: 200 OK
```

```
[{"completed_at":null,"created_at":"2016-03-10T12:32:00-06:00","category":"standard","sourceID":null,"updated_at":"2016-03-14T03:14:17-06:00","service":{"id":21,"name":"Email","localized_name":"Email","provider":{"name":"Widget Data Center, External IT","id":44,"account":{"id":"widget","name":"Widget International"}}},"manager":{"id":37,"name":"Barney Turban","account":{"id":"widget","name":"Widget International"}},"subject":"Upgrade Email servers to Exchange Server 2007 SP2","id":1686,"impact":"top","status":"risk_and_impact","completion_target_at":"2016-03-15T16:33:00-06:00"},"..."]
```

The response contains [these fields](../../workflows.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/workflow_templates/:id/workflows/disabled`: List all disabled workflows of a workflow template with a specific ID
- `/workflow_templates/:id/workflows/enabled`: List all enabled workflows of a workflow template with a specific ID
