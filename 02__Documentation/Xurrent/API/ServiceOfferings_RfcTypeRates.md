# Service Offerings - RFC Type Rates API

## List RFC type rates of a service offering

List all RFC type rates of the service offering with a specific ID.

```
GET /service_offerings/:id/rfc_type_rates
```

### Response

```
status: 200 OK
```

```
[{"id":1,"charge_type":"fixed_price","rate":"150.0","rate_currency":"eur","rfc_type":"emergency_change","nodeID":"..."}]
```

## Add an RFC type rate to a service offering

Add an RFC type rate to a service offering with a specific ID.

```
POST /service_offerings/:id/rfc_type_rates
```

When creating a new RFC type rate for a service offering [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":1,"charge_type":"fixed_price","rate":"150.0","rate_currency":"eur","rfc_type":"emergency_change","nodeID":"..."}
```

## Update an RFC type rate of a service offering

Update an RFC type rate with a specific ID of a service offering with a specific ID.

```
PATCH /service_offerings/:id/rfc_type_rates/:rfc_type_rate_id
```

When updating an existing RFC type rate for a service offering [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":1,"charge_type":"fixed_price","rate":"150.0","rate_currency":"eur","rfc_type":"emergency_change","nodeID":"..."}
```

## Remove an RFC type rate from a service offering

Remove an RFC type rate with a specific ID from a service offering with a specific ID.

```
DELETE /service_offerings/:id/rfc_type_rates/:rfc_type_rate_id
```

### Response

```
status: 204 No Content
```

## Remove all RFC type rates from a service offering

Remove all RFC type rates from a service offering with a specific ID.

```
DELETE /service_offerings/:id/rfc_type_rates
```

### Response

```
status: 204 No Content
```

## Fields

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the RFC type rate.

charge\_type
: *Optional* **[enum](../../general/enumerations/index.html)** — Defines how the RFC type must be charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

rate
: *Conditionally required* **[decimal](../../general/data_types.html)** — The rate per RFC type. Required when `charge_type` is `fixed_price`.

rate\_currency
: *Conditionally required* **[reference](../../general/data_types.html#currency)** — The currency of the rate. Required when `charge_type` is `fixed_price`.

rfc\_type
: *Required* **[reference](../../general/data_types.html#references) to [RFC type](../../rfc_types.html)** — The RFC type related to the RFC type rate.
