# Webhooks API

- [List Webhooks](../events.html#list-webhooks)
- [Get a Webhook](../events.html#get-a-webhook)
- [Create a Webhook](../events.html#create-a-webhook)
- [Edit a Webhook](../events.html#edit-a-webhook)
- [Delete a Webhook](../events.html#delete-a-webhook)
- [Test a Webhook](../events.html#test-a-webhook)
- [Fields](../events.html#fields)
- [Events](../events.html#events)

Only users with the administrator role are authorized to use this API.

## List Webhooks

List all webhooks for an account:

```
GET /webhooks
```

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/webhooks/disabled`: List all disabled webhooks
- `/webhooks/enabled`: List all enabled webhooks

### Response

```
status: 200 OK
```

```
[{"id":2,"name":"Problem Update","event":"problem.update","uri":"https://myserver.example.com/mywebhook","created_at":"2016-03-17T16:36:11-06:00","updated_at":"2016-03-17T17:09:18-06:00"},{"id":1,"name":"Request Team Changed","event":"request.team-changed","uri":"http://postbin.org/axbxd3","disabled":"true","last_error":"404 Not Found","created_at":"2016-03-17T16:34:59-06:00","updated_at":"2016-03-17T16:34:59-06:00"}]
```

## Get a Webhook

```
GET /webhooks/:id
```

### Response

```
status: 200 OK
```

```
{"id":2,"name":"problem.update","event":"problem.update","uri":"https://myserver.example.com/mywebhook","description":"Update requests related to the problem by adding a note.","mail_exceptions_to":"webhook.monitor@example.com","created_at":"2016-03-17T16:36:11-06:00","updated_at":"2016-03-17T17:09:18-06:00"}
```

## Create a Webhook

```
POST /webhooks
```

When creating a new webhook [these fields](../events.html#fields) are available.

```
{"event":"problem.update","uri":"https://myserver.example.com/mywebhook"}
```

### Response

```
status: 200 OK
```

```
{"id":2,"name":"problem.update","event":"problem.update","uri":"https://myserver.example.com/mywebhook","description":"Update requests related to the problem by adding a note.","mail_exceptions_to":"webhook.monitor@example.com","created_at":"2016-03-17T16:36:11-06:00","updated_at":"2016-03-17T17:09:18-06:00"}
```

## Edit a Webhook

```
PATCH /webhooks/:id
```

When updating a new webhook [these fields](../events.html#fields) are available.

```
{"event":"problem.update","uri":"https://myserver.example.com/mywebhook"}
```

### Response

```
status: 200 OK
```

```
{"id":2,"name":"problem.update","event":"problem.update","uri":"https://myserver.example.com/mywebhook","description":"Update requests related to the problem by adding a note.","mail_exceptions_to":"webhook.monitor@example.com","created_at":"2016-03-17T16:36:11-06:00","updated_at":"2016-03-17T17:09:18-06:00"}
```

## Delete a Webhook

```
DELETE /webhooks/:id
```

### Response

```
status: 204 No Content
```

## Test a Webhook

Tests your webhook. You can also test disabled webhooks. When you create a webhook you might want to disable it first, then test until you’re happy, then enable it.

```
POST /webhooks/:id/test
```

### Response

```
status: 204 No Content
```

In addition your script should receive a POST http request with the [webhook contents](../../webhooks.html#webhook-contents). The object\_id will always be equal to 12345 for these tests.

## Fields

app\_offering\_references
: *Optional* array of **[strings](../../general/data_types.html)** — Available for `app_instance` events. This webhook will only be triggered when the App Instance has one of the specified App Offering references.

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the webhook was created.

disabled
: *Optional* **[boolean](../../general/data_types.html)** — Defaults to `false`

description
: *Optional* **[text](../../general/data_types.html) (max 64KB)** — The Description field is used to enter a description of the webhook’s purpose.

description\_attachments
: *Writeonly* **[attachments](../../general/data_types.html#attachments)** The attachments used in the Description field.

event
: *Required* **[string](../../general/data_types.html)** — The event that will trigger this webhook. Valid values are listed [below](../events.html#valid-events).

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the webhook.

mail\_exceptions\_to
: *Optional* **[string](../../general/data_types.html)** — Comma separated list of email addresses who will be informed when the webhook execution fails, e.g. `john.doe@example.com,jane.doe@example.com`.

name
: *Optional* **[string](../../general/data_types.html)** — The name of this webhook. Defaults to the event name.

source
: *Optional* **[string](../../general/data_types.html) (max 30)** - See [source](../../general/source.html)

sourceID
: *Optional* **[string](../../general/data_types.html) (max 128)** - See [source](../../general/source.html)

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the webhook. If the webhook has no updates it contains the `created_at` value.

uri
: *Required* **[string](../../general/data_types.html)** — Publicly accessible URI that Xurrent can use to POST http messages to.

openid\_connect\_discovery
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — The OpenID Connect Discovery box is checked when the public key of the webhook policy should be discoverable via the OpenID Connect Discovery protocol. When enabled, the JWT `iss` (issuer) claim identifies a discovery endpoint from which the public key can be retrieved. See [Automatic Key Discovery](../../webhooks.html#automatic-key-discovery).

webhook\_policy
: *Optional* **[reference](../../general/data_types.html#references) to [Webhook Policy](../../webhook_policies.html)** — The Webhook Policy field is used to select the policy with which to sign the webhook messages.

## Events

Events in Xurrent are identified by the combination of a noun and a verb (i.e. request.create). Note that webhooks are notified when these events occur from within the Xurrent application or from another application that uses the Xurrent API.
The automation\_rule webhook event type can be used to notify webhooks from within [Automation Rules](../../automation_rules.html).

- app\_instance.create
- app\_instance.update
- app\_instance.delete
- app\_instance.secrets-update
- automation\_rule
- broadcast.create
- broadcast.update
- ci.create
- ci.update
- contract.create
- contract.update
- flsa.create
- flsa.update
- knowledge\_article.create
- knowledge\_article.update
- organization.create
- organization.update
- out\_of\_office\_period.create
- out\_of\_office\_period.update
- out\_of\_office\_period.delete
- person.create
- person.update
- problem.create
- problem.manager-changed
- problem.member-changed
- problem.note-added
- problem.status-changed
- problem.team-changed
- problem.update
- product.create
- product.update
- project.create
- project.manager-changed
- project.note-added
- project.status-changed
- project.update
- project\_task.create
- project\_task.note-added
- project\_task.status-changed
- project\_task.update
- release.create
- release.manager-changed
- release.note-added
- release.update
- request.agile-board-column-changed
- request.create
- request.major-incident-status-changed
- request.member-changed
- request.note-added
- request.status-changed
- request.team-changed
- request.update
- risk.create
- risk.update
- risk.note-added
- risk.status-changed
- risk.manager-changed
- service.create
- service.update
- service\_instance.create
- service\_instance.update
- service\_offering.create
- service\_offering.update
- sla.create
- sla.update
- task.create
- task.member-changed
- task.note-added
- task.status-changed
- task.team-changed
- task.update
- team.create
- team.update
- time\_entry.create
- time\_entry.update
- time\_entry.delete
- webhook.verify
- workflow.create
- workflow.manager-changed
- workflow.note-added
- workflow.status-changed
- workflow.update
