# Service Level Agreements - Standard Service Request Activity IDs API

This API works only for service level agreements where you have the Financial Manager role in that account.

## List all standard service request activity IDs of a service level agreement

List all standard service request activity IDs of a service level agreement with a specific ID.

```
GET /slas/:id/standard_service_request_activityIDs
```

### Response

```
status: 200 OK
```

```
[{"activityID":"my-activity-id","id":19,"standard_service_request":{"created_at":"2023-01-24T05:15:07-06:00","id":69,"request_template":{"id":7,"subject":"Add local printer","localized_subject":"Add local printer","nodeID":"..."},"resolution_target":null,"resolution_target_in_days":null,"response_target":null,"response_target_in_days":null,"service_offering":{"id":24,"name":"Bronze Local Printing","service":{"id":26,"name":"Local Printing","localized_name":"Local Printing","nodeID":"...","provider":{"id":63,"name":"Widget Data Center, Internal IT","account":{"id":"widget","name":"Widget International"},"nodeID":"..."}},"nodeID":"..."},"support_hours":null,"updated_at":"2023-01-24T05:15:07-06:00","nodeID":"..."},"nodeID":"..."}]
```

## Add a standard service request activity ID to a service level agreement

Add a standard service request activity ID to a service level agreement with a specific ID.

```
POST /slas/:id/standard_service_request_activityIDs
```

When creating a new standard service request activity ID for a service level agreement [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"activityID":"my-activity-id","id":19,"standard_service_request":{"created_at":"2023-01-24T05:15:07-06:00","id":69,"request_template":{"id":7,"subject":"Add local printer","localized_subject":"Add local printer","nodeID":"..."},"resolution_target":null,"resolution_target_in_days":null,"response_target":null,"response_target_in_days":null,"service_offering":{"id":24,"name":"Bronze Local Printing","service":{"id":26,"name":"Local Printing","localized_name":"Local Printing","nodeID":"...","provider":{"id":63,"name":"Widget Data Center, Internal IT","account":{"id":"widget","name":"Widget International"},"nodeID":"..."}},"nodeID":"..."},"support_hours":null,"updated_at":"2023-01-24T05:15:07-06:00","nodeID":"..."},"nodeID":"..."}
```

## Update a standard service request activity ID of a service level agreement

Update a standard service request activity ID with a specific ID of a service level agreement with a specific ID.

```
PATCH /slas/:id/standard_service_request_activityIDs/:standard_service_request_activityID_id
```

When updating an existing standard service request activity ID for a service level agreement [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"activityID":"my-activity-id","id":19,"standard_service_request":{"created_at":"2023-01-24T05:15:07-06:00","id":69,"request_template":{"id":7,"subject":"Add local printer","localized_subject":"Add local printer","nodeID":"..."},"resolution_target":null,"resolution_target_in_days":null,"response_target":null,"response_target_in_days":null,"service_offering":{"id":24,"name":"Bronze Local Printing","service":{"id":26,"name":"Local Printing","localized_name":"Local Printing","nodeID":"...","provider":{"id":63,"name":"Widget Data Center, Internal IT","account":{"id":"widget","name":"Widget International"},"nodeID":"..."}},"nodeID":"..."},"support_hours":null,"updated_at":"2023-01-24T05:15:07-06:00","nodeID":"..."},"nodeID":"..."}
```

## Remove a standard service request activity ID from a service level agreement

Remove a standard service request activity ID with a specific ID from a service level agreement with a specific ID.

```
DELETE /slas/:id/standard_service_request_activityIDs/:standard_service_request_activityID_id
```

### Response

```
status: 204 No Content
```

## Remove all standard service request activity IDs from a service level agreement

Remove all standard service request activity IDs from a service level agreement with a specific ID.

```
DELETE /slas/:id/standard_service_request_activityIDs
```

### Response

```
status: 204 No Content
```

## Fields

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the standard service request activity ID.

activityID
: *Required* **[string](../../general/data_types.html)** — The Activity ID is the unique identifier by which an activity that is performed in the context of a service offering is known in the billing system of the service provider.

standard\_service\_request
: *Required* **[reference](../../general/data_types.html#references) to [Standard service request](../../standard_service_requests/index.html)** — The standard service request related to the standard service request activity ID.
