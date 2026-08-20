# Workflow Templates - Audit Entries API

## List audit entries of a workflow template

List all [audit entries](../../audit_entries.html) of the workflow template with a specific ID.

```
GET /workflow_templates/:id/audit
```

### Response

```
status: 200 OK
```

```
[{"id":15215,"action":"update","created_at":"2017-01-20T18:50:56-06:00","created_by":{"id":156,"name":"Ellen Brown","account":{"id":"widget","name":"Widget International"}},"changes":{"field2":["Old Value","New Value"]}},{"id":14426,"action":"create","created_at":"2016-12-22T12:13:00-06:00","created_by":{"id":128,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}},"changes":{"field1":[null,"New Value"],"field2":[null,"New Value"],"...":[null,"..."]}}]
```

The response contains [these fields](../../audit_entries.html#fields), except `auditable` and `audited`.
