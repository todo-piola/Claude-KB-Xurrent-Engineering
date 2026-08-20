# Configuration Items - Contracts API

## List all contracts of a configuration item

List all [contracts](../../contracts/index.html) of a configuration item with a specific ID.

```
GET /cis/:id/contracts
```

### Response

```
status: 200 OK
```

```
[{"id":84,"sourceID":null,"name":"0012PQ-MSAS-000605491 - Microsoft Software Assurance Support & Maintenance Agreement","status":"active","category":"support_and_maintenance_contract","created_at":"2016-03-13T02:10:15-05:00","supplier":{"id":27,"name":"Microsoft Corporation"},"updated_at":"2016-03-13T02:10:15-05:00"},{"id":87,"sourceID":null,"name":"0106-SAPUS-00046608 - SAP Enterprise Support for SAP ERP Central Component","status":"active","category":"support_and_maintenance_contract","created_at":"2016-03-13T02:10:15-05:00","supplier":{"id":29,"name":"SAP AG"},"updated_at":"2016-03-13T02:10:15-05:00"},"..."]
```

The response contains [these fields](../../contracts/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/cis/:id/contracts/active`: List all active contracts of a configuration item with a specific ID
- `/cis/:id/contracts/inactive`: List all inactive contracts of a configuration item with a specific ID

## Add a contract to a configuration item

Add a link between a configuration item with a specific ID and a contract with a specific ID.

```
POST /cis/:id/contracts/:contract_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a contract from a configuration item

Remove the link between a configuration item with a specific ID and a contract with a specific ID.

```
DELETE /cis/:id/contracts/:contract_id
```

### Response

```
status: 204 No Content
```

## Remove all contracts from a configuration item

Remove all links between a configuration item with a specific ID and its contracts.

```
DELETE /cis/:id/contracts
```

### Response

```
status: 204 No Content
```
