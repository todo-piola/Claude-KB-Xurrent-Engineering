# Effort Classes - Service Offerings API

## List all service offerings of an effort class

List all [service offerings](../../service_offerings/index.html) of an effort class with a specific ID.

```
GET /effort_classes/:id/service_offerings
```

### Response

```
status: 200 OK
```

```
[{"name":"Bronze Conference Room","created_at":"2016-03-14T03:10:41-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:41-06:00","service":{"name":"Conference Room","id":10,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"id":20,"status":"available"},{"name":"Bronze Local Printing","created_at":"2016-03-14T03:10:41-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:41-06:00","service":{"name":"Local Printing","id":17,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"id":21,"status":"available"},"..."]
```

The response contains [these fields](../../service_offerings/index.html#collection-fields) by default.

## Add a service offering to an effort class

Add a link between an effort class with a specific ID and a service offering with a specific ID.

```
POST /effort_classes/:id/service_offerings/:service_offering_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a service offering from an effort class

Remove the link between an effort class with a specific ID and a service offering with a specific ID.

```
DELETE /effort_classes/:id/service_offerings/:service_offering_id
```

### Response

```
status: 204 No Content
```

## Remove all service offerings from an effort class

Remove all links between an effort class with a specific ID and its service offerings.

```
DELETE /effort_classes/:id/service_offerings
```

### Response

```
status: 204 No Content
```
