# Service Offerings - Standard Service Requests API

- [List all standard service requests of a service offering](index.html#list-all-standard-service-requests-of-a-service-offering)
- [Add a standard service request to a service offering](index.html#add-a-standard-service-request-to-a-service-offering)
- [Update a standard service request of a service offering](index.html#update-a-standard-service-request-of-a-service-offering)
- [Remove a standard service requests from a service offering](index.html#remove-a-standard-service-request-from-a-service-offering)
- [Remove all standard service requests from a service offering](index.html#remove-all-standard-service-requests-from-a-service-offering)
- [Fields](index.html#fields)

## List all standard service requests of a service offering

List all [standard service requests](../../standard_service_requests/index.html) of the service offering with a specific ID:

```
GET /service_offerings/:id/standard_service_requests
```

### Response

```
status: 200 OK
```

```
[{"id":1,"created_at":"2016-08-23T13:43:01-07:00","updated_at":"2016-08-23T13:43:01-07:00","request_template":{"id":5,"subject":"Creation or modification of ITRP report","localized_subject":"Creation or modification of ITRP report"},"response_target":60,"resolution_target":null,"support_hours":{"name":"Monday through Friday, 7:00am until 5:00pm","id":86}},{"id":15,"created_at":"2016-03-13T19:22:40-07:00","updated_at":"2016-03-13T19:22:40-07:00","request_template":{"id":6,"subject":"Request for information concerning ITRP","localized_subject":"Request for information concerning ITRP"},"response_target":5,"resolution_target":12,"support_hours":{"name":"24x7 (Monday through Sunday)","id":85}}]
```

The response contains [these fields](../../standard_service_requests/index.html#fields) by default.

### Sorting

By default a collection of standard service requests is sorted **descending** by `id`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../../general/ordering.html):

`id` `created_at` `updated_at`

## Add a standard service request to a service offering

Add a standard service request to a service offering with a specific ID.

```
POST /service_offerings/:id/standard_service_requests
```

When creating a new standard service request for a service offering [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"2015-04-09T02:43:20-07:00","id":19,"request_template":{"id":25,"subject":"Move Personal Computer","localized_subject":"Move Personal Computer"},"resolution_target":480,"response_target":120,"support_hours":{"id":34,"name":"Monday through Friday, 7:00am until 5:00pm"},"updated_at":"2015-04-09T02:43:20-07:00"}
```

## Update a standard service request of a service offering

Update a standard service request with a specific ID of a service offering with a specific ID.

```
PATCH /service_offerings/:id/standard_service_requests/:standard_service_request_id
```

When updating an existing standard service request for a service offering [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"2015-04-09T02:43:20-07:00","id":19,"request_template":{"id":25,"subject":"Move Personal Computer","localized_subject":"Move Personal Computer"},"resolution_target":480,"response_target":120,"support_hours":{"id":34,"name":"Monday through Friday, 7:00am until 5:00pm"},"updated_at":"2015-04-09T02:43:20-07:00"}
```

## Remove a standard service request from a service offering

Remove a standard service request with a specific ID from a service offering with a specific ID.

```
DELETE /service_offerings/:id/standard_service_requests/:standard_service_request_id
```

### Response

```
status: 204 No Content
```

## Remove all standard service requests from a service offering

Remove all standard service requests from a service offering with a specific ID.

```
DELETE /service_offerings/:id/standard_service_requests
```

### Response

```
status: 204 No Content
```

## Fields

charge\_type
: *Optional* **[enum](../../general/enumerations/index.html)** — Defines how the standard service request must be charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the standard service request was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the service level agreement.

rate
: *Optional* **[decimal](../../general/data_types.html)** — Defines the fixed price rate for the standard service request.

rate\_currency
: *Optional* **[reference](../../general/data_types.html#currency)** — Defines the currency for the fixed price rate of the standard service request.

request\_template
: *Required* **[reference](../../general/data_types.html#references) to [Request template](../../request_templates.html)** — The ID of the request template related to the service offering. Only the request templates that are linked to the same service as the service offering can be selected.

response\_target
: *Optional* **[integer](../../general/data_types.html)** — Number of minutes within which a response needs to have been provided for a request to which the request template has been applied and which requester is covered by an SLA that is based on the service offering.

response\_target\_best\_effort
: *Optional* **[boolean](../../general/data_types.html)** — Response target is Best Effort when the request template has been applied to the request and the requester is covered by an SLA that is based on the service offering.

response\_target\_notification\_scheme
: Optional **[reference](../../general/data_types.html#references) to [SLA notification scheme](../../sla_notification_schemes/index.html)** — The ID of the response target notification scheme for a request when it affects
 an active SLA that is based on the service offering. Only enabled SLA notification schemes that are linked to the same account as the service offering can be selected.

resolution\_target
: *Optional* **[integer](../../general/data_types.html)** — Number of minutes within which a request needs to have been completed when the request template has been applied to the request and the requester is covered by an SLA that is based on the service offering.

resolution\_target\_best\_effort
: *Optional* **[boolean](../../general/data_types.html)** — Resolution target is Best Effort when the request template has been applied to the request and the requester is covered by an SLA that is based on the service offering.

resolution\_target\_notification\_scheme
: Optional **[reference](../../general/data_types.html#references) to [SLA notification scheme](../../sla_notification_schemes/index.html)** — The ID of the resolution target notification scheme for a request when it affects
 an active SLA that is based on the service offering. Only enabled SLA notification schemes that are linked to the same account as the service offering can be selected.

support\_hours
: *Optional* **[reference](../../general/data_types.html#references) to [Calendar](../../calendars/index.html)** — The ID of the calendar that defines the support hours for a request to which the request template has been applied and which requester is covered by an SLA that is based on the service offering.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the standard service request. If the standard service request has no updates it contains the `created_at` value.

sla\_notification\_scheme
: Optional **[reference](../../general/data_types.html#references) to [SLA notification scheme](../../sla_notification_schemes/index.html)** — The ID of the SLA notification scheme for a request when it affects
 an active SLA that is based on the service offering. Only enabled SLA notification schemes that are linked to the same account as the service offering can be selected. **Deprecated**: use `resolution_target_notification_scheme` instead.
