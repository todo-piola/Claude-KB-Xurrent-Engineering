# Shop Articles - Service Offerings API

## List service offerings of a shop article

List all [service offerings](../../service_offerings/index.html) of the shop article with a specific ID.

```
GET /shop_articles/:id/service_offerings
```

### Response

```
status: 200 OK
```

```
[{"name":"Bronze Conference Room","created_at":"2016-03-14T03:10:41-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:41-06:00","service":{"name":"Conference Room","id":10,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"id":20,"status":"available"},{"name":"Bronze Local Printing","created_at":"2016-03-14T03:10:41-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:41-06:00","service":{"name":"Local Printing","id":17,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"id":21,"status":"available"},"..."]
```

The response contains [these fields](../../service_offerings/index.html#collection-fields) by default.
