# Service Level Agreements - Effort Class Rate IDs API

This API works only for service level agreements where you have the Financial Manager role in that account.

## List all effort class rate IDs of a service level agreement

List all effort class rate IDs of a service level agreement with a specific ID.

```
GET /slas/:id/effort_class_rateIDs
```

### Response

```
status: 200 OK
```

```
[{"id":97,"nodeID":"...","rateID":"rate-identifier","effort_class":{"id":10,"name":"Billable Project Management - Business Hours","account":{"id":"widget","name":"Widget International"},"nodeID":"..."}}]
```

## Add an effort class rate ID to a service level agreement

Add an effort class rate ID to a service level agreement with a specific ID.

```
POST /slas/:id/effort_class_rateIDs
```

When creating a new effort class rate ID for a service level agreement [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"rateID":"rate-123","effort_class":{"id":10,"name":"Billable Project Management - Business Hours","account":{"id":"widget","name":"Widget International"},"nodeID":"..."},"id":100,"nodeID":"..."}
```

## Update an effort class rate ID of a service level agreement

Update an effort class rate ID with a specific ID of a service level agreement with a specific ID.

```
PATCH /slas/:id/effort_class_rateIDs/:effort_class_rateID_id
```

When updating an existing effort class rate ID for a service level agreement [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"rateID":"rate-123","effort_class":{"id":10,"name":"Billable Project Management - Business Hours","account":{"id":"widget","name":"Widget International"},"nodeID":"..."},"id":100,"nodeID":"..."}
```

## Remove an effort class rate ID from a service level agreement

Remove an effort class rate ID with a specific ID from a service level agreement with a specific ID.

```
DELETE /slas/:id/effort_class_rateIDs/:effort_class_rateID_id
```

### Response

```
status: 204 No Content
```

## Remove all effort class rate IDs from a service level agreement

Remove all effort class rate IDs from a service level agreement with a specific ID.

```
DELETE /slas/:id/effort_class_rateIDs
```

### Response

```
status: 204 No Content
```

## Fields

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the effort class rate ID.

rateID
: *Required* **[string](../../general/data_types.html)** — The Rate ID is the unique identifier by which an effort class that is linked to a time entry when an activity was performed through the coverage of the SLA is known in the billing system of the service provider.

effort\_class
: *Required* **[reference](../../general/data_types.html#references) to [Effort class](../../effort_classes.html)** — The effort class related to the effort class rate ID.
