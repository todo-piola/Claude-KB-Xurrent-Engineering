# Releases - Workflows API

## List all workflows of a release

List all [workflows](../../workflows.html) of a release with a specific ID.

```
GET /releases/:id/workflows
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

- `/releases/:id/workflows/completed`: List all completed workflows of a release with a specific ID
- `/releases/:id/workflows/open`: List all open workflows of a release with a specific ID

## Add a workflow to a release

Add a link between a release with a specific ID and a workflow with a specific ID.

```
POST /releases/:id/workflows/:workflow_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a workflow from a release

Remove the link between a release with a specific ID and a workflow with a specific ID.

```
DELETE /releases/:id/workflows/:workflow_id
```

### Response

```
status: 204 No Content
```

## Remove all workflows from a release

Remove all links between a release with a specific ID and its workflows.

```
DELETE /releases/:id/workflows
```

### Response

```
status: 204 No Content
```
