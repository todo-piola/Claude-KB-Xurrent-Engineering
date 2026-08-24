# App Offerings API

- [List app offerings](index.html#list-app-offerings)
- [Get a single app offering](index.html#get-a-single-app-offering)
- [Create an app offering](index.html#create-an-app-offering)
- [Update an app offering](index.html#update-an-app-offering)
- [Fields](index.html#fields)

## List app offerings

List all app offerings for an account:

```
GET /app_offerings
```

### Response

```
status: 200 OK
```

```
[{"id":1,"sourceID":null,"reference":"note-dispatcher","name":"Log Note Dispatcher Integration","created_at":"2021-04-13T04:19:49-05:00","updated_at":"2021-04-13T04:19:51-05:00","service_instance":{"id":83,"name":"Our Integration"},"policy_jwt_alg":"rs512","webhook_uri_template":"https://jfgd645.execute-api.eu-west-1.amazonaws.com/Prod/integration/?account={account}","...":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of app offerings.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/app_offerings/latest_internal`: List all draft app offerings in the current account
- `/app_offerings/latest_published`: List the latest version of each app offering published by the current account
- `/app_offerings/all_latest_published`: List the latest version of each app offering published by the current account and its trusted accounts
- `/app_offerings/consumed`: List all app offerings installed in the current account

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of app offerings:

`created_at` `id` `name` `nodeID` `policy_jwt_alg` `policy_jwt_audience` `policy_jwt_claim_expires_in` `reference`
`service_instance` `sourceID` `updated_at` `webhook_uri_template`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `reference` `name` `created_at` `updated_at` `disabled`

### Sorting

By default a collection of app offerings is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name`, `created_at` `updated_at`

## Get a single app offering

```
GET /app_offerings/:id
```

### Response

```
status: 200 OK
```

```
{"id":1,"sourceID":null,"reference":"note-dispatcher","name":"Log Note Dispatcher Integration","created_at":"2021-04-13T04:19:49-05:00","updated_at":"2021-04-13T04:19:51-05:00","service_instance":{"id":83,"name":"Our Integration"},"policy_jwt_alg":"rs512","webhook_uri_template":"https://jfgd645.execute-api.eu-west-1.amazonaws.com/Prod/integration/?account={account}","...":"..."}
```

The response contains [these fields](index.html#fields).

## Create an app offering

```
POST /app_offerings
```

When creating a new app offering [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created app offering and is similar to the response in [Get a single app offering](index.html#get-a-single-app-offering).

## Update an app offering

```
PATCH /app_offerings/:id
```

When updating an app offering [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated integration and is similar to the response in [Get a single app offering](index.html#get-a-single-app-offering).

## Fields

attachments
: *Readonly* **aggregated Attachments**

card\_description
: *Optional* **[string](../general/data_types.html) (max 255)** — Short description of the app offering to be shown on the card in the App store.

configuration\_uri\_template
: *Optional* **[string](../general/data_types.html) (max 255)** — The URI where the app can be configured. The placeholder `{account}` can be used to include the customer account id in the URI.

compliance
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Compliance field is used to enter the compliance statement for the app offering. This is shown to customers on the ‘Security & Compliance’ tab in the Apps section for this app.

compliance\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Compliance field.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the app offering was created.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to enter a description of the app offering. This is shown to customers on its own tab in the Apps section for this app.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the app may no longer be installed by new customers. Customers that have an older version installed can still update when the app offering is disabled.

features
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Feature field is used to elaborate on the features of the app offering. This is shown to customers on its own tab in the Apps section for this app.

features\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Features field.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the app offering.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the app offering.

openid\_connect\_discovery
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether the webhook for this app uses OpenID Connect Discovery to allow retrieval of the policy’s public key via a JWKS endpoint.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the app offering. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

policy\_jwt\_alg
: *Required* **[enum](../general/enumerations/index.html)** — The algorithm used for generating the policy for the app’s webhook. Valid values are:

 - `rs256`: RSA using SHA-256
 - `rs384`: RSA using SHA-384
 - `rs512`: RSA using SHA-512
 - `es256`: ECDSA using P-256 and SHA-256
 - `es384`: ECDSA using P-384 and SHA-384
 - `es512`: ECDSA using P-521 and SHA-512

policy\_jwt\_audience
: *Optional* **[string](../general/data_types.html) (max 2KB)** — The audience for the policy for the app’s webhook.

policy\_jwt\_claim\_expires\_in
: *Optional* **[duration](../general/data_types.html)** — The claim expiry time for the policy for the app’s webhook.

reference
: *Required* **[string](../general/data_types.html) (max 161)** — The Reference field can be used to identify the app offering via the APIs, it is the only identifier that will remain stable across version updates. It may only be changed until the app offering is published for the first time. The Reference field defaults to the Name field value, written in lower case characters and with all spaces replaced by the underscore character, prefixed with the account name followed with an underscore (e.g. `wdc_`). It must be unique across all accounts.

requires\_enabled\_oauth\_person
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — This app requires an enabled OAuth person, which makes it @mentionable and visible like a real person..

service\_instance
: *Required* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The Service instance field is used to select the [Service Instance](../service_instances/index.html) that should be used when creating Requests regarding this app offering.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

ui\_extension\_version
: *Optional* **[reference](../general/data_types.html#references) to [UI Extension Version](../ui_extensions/versions.html)** — The UI extension version field is used to select the (version of the) UI extension for this app offering’s instances. The UI extension is shown on the ‘Configuration’ tab in the Apps section for customers that install this app offering.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the integration. If the app offering has no updates it contains the `created_at` value.

webhook\_uri\_template
: *Required* **[string](../general/data_types.html) (max 255)** — The URI for the app’s webhook. The placeholder `{account}` can be used to include the customer account id in the URI.
