# Projects - Workflows API

## List all workflows of a project

List all [workflows](../../workflows.html) of a project with a specific ID.

```
GET /projects/:id/workflows
```

### Response

```
status: 200 OK
```

```
[{"completed_at":null,"created_at":"2016-03-10T12:32:00-06:00","category":"standard","sourceID":null,"updated_at":"2016-03-14T03:14:17-06:00","service":{"id":21,"name":"Email","localized_name":"Email","provider":{"name":"Widget Data Center, External IT","id":44,"account":{"id":"widget","name":"Widget International"}}},"manager":{"id":37,"name":"Barney Turban","account":{"id":"widget","name":"Widget International"}},"subject":"Upgrade Email servers to Exchange Server 2007 SP2","id":1686,"impact":"top","status":"risk_and_impact","completion_target_at":"2016-03-15T16:33:00-06:00"},"..."]
```

The response contains [these fields](../../workflows.html#collection-fields) by default.

## Add a workflow to a project

Add a link between a project with a specific ID and a workflow with a specific ID.

```
POST /projects/:id/workflows/:workflow_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a workflow from a project

Remove the link between a project with a specific ID and a workflow with a specific ID.

```
DELETE /projects/:id/workflows/:workflow_id
```

### Response

```
status: 204 No Content
```

## Remove all workflows from a project

Remove all links between a project with a specific ID and its workflows.

```
DELETE /projects/:id/workflows
```

### Response

```
status: 204 No Content
```
