# App Offerings - App Instances API

## List app instances of an app offering

List all [app instances](../../app_instances/index.html) of the app offering with a specific ID.

```
GET /app_offerings/:id/app_instances
```

### Response

```
status: 200 OK
```

```
[{"id":1,"app_offering":{"reference":"note-dispatcher","id":1},"customer_account":{"id":"wdc","name":"Widget Data Center"},"created_at":"2021-04-13T04:36:10-05:00","updated_at":"2021-04-13T04:36:10-05:00","enabled_by_customer":true,"...":"..."},"..."]
```

The response contains [these fields](../../app_instances/index.html#collection-fields) by default.
