# App Offerings - Automation Rules API

## List automation rules of an app offering

List all [app offering automation rules](../../app_offering_automation_rules/index.html) of the integration with a specific ID.

```
GET /app_offerings/:id/automation_rules
```

### Response

```
status: 200 OK
```

```
[{"id":1,"app_offering":{"reference":"note-dispatcher","id":1},"rulable_type":"Req","name":"Trigger webhook for each note added","trigger":"on note added","position":1,"created_at":"2021-04-13T04:19:50-05:00","updated_at":"2021-04-13T04:19:50-05:00","...":"..."},"..."]
```

The response contains [these fields](../../app_offering_automation_rules/index.html#collection-fields) by default.
