# Service Level Agreements - RFC Type Activity IDs API

This API works only for service level agreements where you have the Financial Manager role in that account.

## List all RFC type activity IDs of a service level agreement

List all RFC type activity IDs of a service level agreement with a specific ID.

```
GET /slas/:id/rfc_type_activityIDs
```

### Response

```
status: 200 OK
```

```
[{"activityID":"rfc-type-act-1","id":1,"rfc_type":"emergency_change","nodeID":"..."}]
```

## Add an RFC type activity ID to a service level agreement

Add an RFC type activity ID to a service level agreement with a specific ID.

```
POST /slas/:id/rfc_type_activityIDs
```

When creating a new RFC type activity ID for a service level agreement [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"activityID":"rfc-type-act-1","id":1,"rfc_type":"emergency_change","nodeID":"..."}
```

## Update an RFC type activity ID of a service level agreement

Update an RFC type activity ID with a specific ID of a service level agreement with a specific ID.

```
PATCH /slas/:id/rfc_type_activityIDs/:rfc_type_activityID_id
```

When updating an existing RFC type activity ID for a service level agreement [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"activityID":"rfc-type-act-1","id":1,"rfc_type":"emergency_change","nodeID":"..."}
```

## Remove an RFC type activity ID from a service level agreement

Remove an RFC type activity ID with a specific ID from a service level agreement with a specific ID.

```
DELETE /slas/:id/rfc_type_activityIDs/:rfc_type_activityID_id
```

### Response

```
status: 204 No Content
```

## Remove all RFC type activity IDs from a service level agreement

Remove all RFC type activity IDs from a service level agreement with a specific ID.

```
DELETE /slas/:id/rfc_type_activityIDs
```

### Response

```
status: 204 No Content
```

## Fields

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the RFC type activity ID.

activityID
: *Required* **[string](../../general/data_types.html)** — The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider.

rfc\_type
: *Required* **[reference](../../general/data_types.html#references) to [RFC type](../../rfc_types.html)** — The RFC type related to the RFC type activity ID.
