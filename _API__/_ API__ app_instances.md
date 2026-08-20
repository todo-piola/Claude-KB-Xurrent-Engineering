# App Instances API

- [List app instances](index.html#list-app-instances)
- [Get a single app instance](index.html#get-a-single-app-instance)
- [Create an app instance](index.html#create-an-app-instance)
- [Update an app instance](index.html#update-an-app-instance)
- [Fields](index.html#fields)

## List app instances

List all app instances for an account:

```
GET /app_instances
```

### Response

```
status: 200 OK
```

```
[{"id":1,"app_offering":{"reference":"note-dispatcher","id":1},"customer_account":{"id":"wdc","name":"Widget Data Center"},"created_at":"2021-04-13T04:36:10-05:00","updated_at":"2021-04-13T04:36:10-05:00","enabled_by_customer":true,"...":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of app instances.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/app_instances/enabled`: List all enabled app instances
- `/app_instances/disabled`: List all disabled app instances

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of app instances:

`created_at` `id` `nodeID` `updated_at` `disabled` `customer_account` `app_offering` `enabled_by_customer`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `created_at` `updated_at` `disabled`

### Sorting

By default a collection of apps instances is not sorted.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `created_at` `updated_at`

## Get a single app instance

```
GET /app_instances/:id
```

### Response

```
status: 200 OK
```

```
{"id":1,"app_offering":{"reference":"note-dispatcher","id":1},"customer_account":{"id":"wdc","name":"Widget Data Center"},"created_at":"2021-04-13T04:36:10-05:00","updated_at":"2021-04-13T04:36:10-05:00","enabled_by_customer":true,"...":"..."}
```

The response contains [these fields](index.html#fields).

## Create an app instance

```
POST /app_instances
```

When creating a new app instance [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created app instance and is similar to the response in [Get a single app instance](index.html#get-a-single-app-instance).

## Update an app instance

```
PATCH /app_instances/:id
```

When updating an app instance [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated app instance and is similar to the response in [Get a single app instance](index.html#get-a-single-app-instance).

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the app instance was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension version](../ui_extensions/versions.html) that is linked to the app offering.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

customer\_account
: *Readonly* **[reference](../general/data_types.html#references) to [Account](../account.html)** — Account this app instance is for.

customer\_representative
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The contact person regarding this app instance.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the app instance is disabled by the provider of the Integration. This means the automation rules, webhook, application token of the instance in the customer’s account are disabled.

enabled\_by\_customer
: *Optional* **[boolean](../general/data_types.html)** — The Enabled by customer box is checked when the customer allows the app to operate in their account. This means the automation rules, webhook, application token of the instance in the customer’s account are enabled.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the app instance.

app\_offering
: *Required* **[reference](../general/data_types.html#references) to [App Offering](../app_offerings/index.html)** — This field references the App Offering this instance belongs to.

suspended
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Suspended box must be checked when either the provider or customer wants to disable the app instance, but the other party is allowed to enable it again. This means the automation rules, webhook, application token of the instance in the customer’s account are disabled.

suspension\_comment
: *Optional* **[string](../general/data_types.html) (max 64KB)** — The Suspension comment field is used to describe why the app instance was suspended.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the app instance. If the app instance has no updates it contains the `created_at` value.

webhook
: *Optional* **[reference](../general/data_types.html#references) to [Webhook](../webhooks.html)** — This field references the webhook created for the app in the customer’s account.

webhook\_policy
: *Optional* **[reference](../general/data_types.html#references) to [Webhook Policy](../webhook_policies.html)** — This field references the webhook policy created for the app in the customer’s account.
