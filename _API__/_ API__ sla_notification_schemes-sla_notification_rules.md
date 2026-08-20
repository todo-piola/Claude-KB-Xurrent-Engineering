# SLA Notification Schemes - SLA Notification Rules API

- [List all SLA notification rules of an SLA notification scheme](index.html#list-all-sla-notification-rules-of-an-sla-notification-scheme)
- [Get a single SLA notification rule of an SLA notification scheme](index.html#get-a-single-sla-notification-rule-of-an-sla-notification-scheme)
- [Add an SLA notification rule to an SLA notification scheme](index.html#add-an-sla-notification-rule-to-an-sla-notification-scheme)
- [Update an SLA notification rule of an SLA notification scheme](index.html#update-an-sla-notification-rule-of-an-sla-notification-scheme)
- [Remove an SLA notification rule from an SLA notification scheme](index.html#remove-an-sla-notification-rule-from-an-sla-notification-scheme)
- [Remove all SLA notification rules from an SLA notification scheme](index.html#remove-all-sla-notification-rules-from-an-sla-notification-scheme)
- [Fields](index.html#fields)

## List all SLA notification rules of an SLA notification scheme

List all SLA notification rules of an SLA notification scheme with a specific ID.

```
GET /sla_notification_schemes/:id/sla_notification_rules
```

### Response

```
status: 200 OK
```

```
[{"id":1,"threshold_percentage":25,"notify_current_assignee":true,"notify_service_owner":false,"notify_support_team_manager":false,"notify_support_team_coordinator":false,"notify_first_line_team_manager":false,"notify_first_line_team_coordinator":false,"created_at":"2022-11-24T18:39:44-06:00","updated_at":"2022-11-24T18:39:44-06:00"},{"id":2,"threshold_percentage":50,"notify_current_assignee":false,"notify_service_owner":true,"notify_support_team_manager":true,"notify_support_team_coordinator":false,"notify_first_line_team_manager":false,"notify_first_line_team_coordinator":false,"created_at":"2022-11-24T18:39:44-06:00","updated_at":"2022-11-24T18:39:44-06:00"}]
```

The response contains [these fields](index.html#fields) by default.

## Get a single SLA notification rule of an SLA notification scheme

```
GET /sla_notification_schemes/:id/sla_notification_rules/:rule_id
```

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [these fields](index.html#fields).

## Add an SLA notification rule to an SLA notification scheme

Add a new SLA notification rule to an SLA notification scheme with a specific ID.

```
POST /sla_notification_schemes/:id/sla_notification_rules
```

When adding a new rule to an SLA notification scheme [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created SLA notification rule and is similar to the response in [Get a single SLA notification rule of an SLA notification scheme](index.html#get-a-single-sla-notification-rule-of-an-sla-notification-scheme).

## Update an SLA notification rule of an SLA notification scheme

Update an SLA notification rule with a specific ID of an SLA notification scheme with a specific ID.

```
PATCH /sla_notification_schemes/:id/sla_notification_rules/:rule_id
```

When updating an existing SLA notification rule [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated SLA notification rule and is similar to the response in [Get a single SLA notification rule of an SLA notification scheme](index.html#get-a-single-sla-notification-rule-of-an-sla-notification-scheme).

## Remove an SLA notification rule from an SLA notification scheme

Remove the link between an SLA notification scheme with a specific ID and an SLA notification rule with a specific ID.

```
DELETE /sla_notification_schemes/:id/sla_notification_rules/:rule_id
```

### Response

```
status: 204 No Content
```

## Remove all SLA notification rules from an SLA notification scheme

Remove all links between an SLA notification scheme with a specific ID and its SLA notification rules.

```
DELETE /sla_notification_schemes/:id/sla_notification_rules
```

### Response

```
status: 204 No Content
```

## Fields

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the SLA notification rule was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the SLA notification rule.

notify\_current\_assignee
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — Whether to notify the current assignee of the request.

notify\_first\_line\_team\_coordinator
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — Whether to notify the first line team coordinator of the service instance of the affected SLA.

notify\_first\_line\_team\_manager
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — Whether to notify the first line team manager of the service instance of the affected SLA.

notify\_service\_owner
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — Whether to notify the service owner of the service of the affected SLA.

notify\_support\_team\_coordinator
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — Whether to notify the support team coordinator of the service instance of the affected SLA.

notify\_support\_team\_manager
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — Whether to notify the support team manager of the service instance of the affected SLA.

threshold\_percentage
: *Required* **[integer](../../general/data_types.html)** — The percentage of the resolution target duration when a notification should be generated.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the SLA notification rule. If the SLA notification rule has no updates it contains the `created_at` value.
