# Service Offerings - Effort Class Rates API

## List effort class rates of a service offering

List all effort class rates of the service offering with a specific ID.

```
GET /service_offerings/:id/effort_class_rates
```

### Response

```
status: 200 OK
```

```
[{"effort_class":{"id":4,"name":"Billable Support - Business Hours","account":{"id":"widget","name":"Widget International"},"nodeID":"..."},"id":1,"rate":"60.0","rate_currency":"eur","nodeID":"..."}]
```

## Add an effort class rate to a service offering

Add an effort class rate to a service offering with a specific ID.

```
POST /service_offerings/:id/effort_class_rates
```

When creating a new effort class rate for a service offering [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"effort_class":{"id":4,"name":"Billable Support - Business Hours","account":{"id":"widget","name":"Widget International"},"nodeID":"..."},"id":1,"rate":"60.0","rate_currency":"eur","nodeID":"..."}
```

## Update an effort class rate of a service offering

Update an effort class rate with a specific ID of a service offering with a specific ID.

```
PATCH /service_offerings/:id/effort_class_rates/:effort_class_rate_id
```

When updating an existing effort class rate for a service offering [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"effort_class":{"id":4,"name":"Billable Support - Business Hours","account":{"id":"widget","name":"Widget International"},"nodeID":"..."},"id":1,"rate":"60.0","rate_currency":"eur","nodeID":"..."}
```

## Remove an effort class rate from a service offering

Remove an effort class rate with a specific ID from a service offering with a specific ID.

```
DELETE /service_offerings/:id/effort_class_rates/:effort_class_rate_id
```

### Response

```
status: 204 No Content
```

## Remove all effort class rates from a service offering

Remove all effort class rates from a service offering with a specific ID.

```
DELETE /service_offerings/:id/effort_class_rates
```

### Response

```
status: 204 No Content
```

## Fields

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the effort class rate.

effort\_class
: *Required* **[reference](../../general/data_types.html#references) to [Effort class](../../effort_classes.html)** — The ID of the effort class related to the effort class rate.

rate
: *Required* **[decimal](../../general/data_types.html)** — The rate per hour for the effort class.

rate\_currency
: *Required* **[reference](../../general/data_types.html#currency)** — The currency of the rate per hour for the effort class.
