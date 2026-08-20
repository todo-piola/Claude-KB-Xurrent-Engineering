# Agile Boards - Customer Representative SLAs API

## List all service level agreements of an agile board

List all [service level agreements](../../service_level_agreements.html) whose customer representatives can access an agile board with a specific ID.

```
GET /agile_boards/:id/customer_representative_slas
```

### Response

```
status: 200 OK
```

```
[{"name":"BlackBerry Standard Smart Phone for Widget Data Center, External IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":145,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},{"name":"BlackBerry Standard Smart Phone for Widget Data Center, Internal IT","created_at":"2016-03-14T03:10:46-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:46-06:00","account":{"name":"Widget North America","id":"wna"},"id":146,"service_offering":{"name":"BlackBerry Standard Smart Phone","service":{"name":"Smart Phone","account":{"name":"Widget North America","id":"wna"},"id":45,"provider":{"name":"Widget North America, Information Technology","account":{"name":"Widget North America","id":"wna"},"id":45}},"account":{"name":"Widget North America","id":"wna"},"id":62},"status":"active"},"..."]
```

The response contains [these fields](../../service_level_agreements.html#collection-fields) by default.

## Add a service level agreement to an agile board

Add a link between an agile board with a specific ID and a service level agreement with a specific ID.

```
POST /agile_boards/:id/customer_representative_slas/:service_level_agreement_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a service level agreement from an agile board

Remove the link between an agile board with a specific ID and a service level agreement with a specific ID.

```
DELETE /agile_boards/:id/customer_representative_slas/:service_level_agreement_id
```

### Response

```
status: 204 No Content
```

## Remove all service level agreements from an agile board

Remove all service level agreement links from an agile board with a specific ID.

```
DELETE /agile_boards/:id/customer_representative_slas
```

### Response

```
status: 204 No Content
```
