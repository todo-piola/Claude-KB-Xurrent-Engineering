# Workflows - Problems API

## List all problems of a workflow

List all [problems](../../problems.html) of a workflow with a specific ID.

```
GET /workflows/:id/problems
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2016-03-13T10:27:00-06:00","analysis_target_at":"2016-03-20T03:00:00-06:00","sourceID":null,"updated_at":"2016-03-14T03:14:13-06:00","service":{"name":"Expense Reporting","id":14,"provider":{"name":"Widget Data Center, External IT","id":30}},"member":{"name":"Tom Waters","id":36},"solved_at":null,"subject":"Clicking on the Submit button does not submit new expense report","id":221,"impact":"top","team":{"name":"Application Development","id":7},"status":"in_progress"},"..."]
```

The response contains [these fields](../../problems.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/workflows/:id/problems/active`: List all active problems of a workflow with a specific ID
- `/workflows/:id/problems/known_errors`: List all known errors of a workflow with a specific ID
- `/workflows/:id/problems/progress_halted`: List all halted problems of a workflow with a specific ID
- `/workflows/:id/problems/solved`: List all solved problems of a workflow with a specific ID

## Add a problem to a workflow

Add a link between a workflow with a specific ID and a problem with a specific ID.

```
POST /workflows/:id/problems/:problem_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a problem from a workflow

Remove the link between a workflow with a specific ID and a problem with a specific ID.

```
DELETE /workflows/:id/problems/:problem_id
```

### Response

```
status: 204 No Content
```

## Remove all problems from a workflow

Remove all links between a workflow with a specific ID and its problems.

```
DELETE /workflows/:id/problems
```

### Response

```
status: 204 No Content
```
