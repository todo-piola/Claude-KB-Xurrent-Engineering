# Organizations - Contracts API

## List all contracts of an organization

List all [contracts](../../contracts/index.html) of an organization with a specific ID.

```
GET /organizations/:id/contracts
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

- `/organizations/:id/contracts/active`: List all active contracts of an organization with a specific ID
- `/organizations/:id/contracts/inactive`: List all inactive contracts of an organization with a specific ID
