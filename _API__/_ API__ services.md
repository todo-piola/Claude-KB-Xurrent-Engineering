# Services API

- [List services](../services.html#list-services)
- [Get a single service](../services.html#get-a-single-service)
- [Create a service](../services.html#create-a-service)
- [Update a service](../services.html#update-a-service)
- [Fields](../services.html#fields)

## List services

List all services for an account:

```
GET /services
```

### Response

```
status: 200 OK
```

```
[{"name":"Conference Room","created_at":"2016-03-14T03:10:37-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:37-06:00","support_team":{"name":"End-User Support, Houston","id":9},"id":10,"disabled":false,"provider":{"name":"Widget Data Center, Internal IT","id":32}},{"name":"Customer Relationship Management (Siebel)","created_at":"2016-03-14T03:10:37-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:37-06:00","support_team":{"name":"Application Development","id":7},"id":11,"disabled":false,"provider":{"name":"Widget Data Center, External IT","id":30}},"..."]
```

The response contains [these fields](../services.html#collection-fields) by default. [Filtering](../services.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of services.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/services/disabled`: List all disabled services
- `/services/enabled`: List all enabled services

### Collection Fields

By default the following [fields](../services.html#fields) will appear in collections of services:

`id` `sourceID` `name` `provider` `support_team` `created_at` `updated_at`

Obtain a different set of [fields](../services.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../services.html#fields):

`id` `source` `sourceID` `name` `disabled` `provider` `support_team` `created_at` `updated_at`

### Sorting

By default a collection of services is sorted **ascending** by `name`.

The following [fields](../services.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `provider` `support_team` `created_at` `updated_at`

## Get a single service

```
GET /services/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"knowledge_manager":{"id":75,"name":"Barney Turban","account":{"id":"widget","name":"Widget International"}},"availability_manager":{"id":75,"name":"Barney Turban","account":{"id":"widget","name":"Widget International"}},"capacity_manager":{"id":75,"name":"Barney Turban","account":{"id":"widget","name":"Widget International"}},"change_manager":{"id":212,"name":"Grace Weller","account":{"id":"widget","name":"Widget International"}},"continuity_manager":{"id":353,"name":"Luis Thomas","account":{"id":"widget","name":"Widget International"}},"created_at":"2017-05-21T18:34:09-05:00","description":"The Email service provides the ability to send email messages to, and receive emails from, email users within the organization and email users connected to the internet.","disabled":false,"first_line_team":{"id":2,"name":"Service Desk","account":{"id":"virtualsupport","name":"VirtualSupport"}},"id":21,"impact":"low","name":"Email","picture_uri":"https://itrp-demo-defaults.s3.amazonaws.com/avatars/services/original/email3.svg","problem_manager":{"id":75,"name":"Barney Turban","account":{"id":"widget","name":"Widget International"}},"provider":{"id":44,"name":"Widget Data Center, External IT","account":{"id":"widget","name":"Widget International"}},"release_manager":{"id":281,"name":"Jo-Ann Stock","account":{"id":"widget","name":"Widget International"}},"service_category":{"id":8,"name":"Communication","localized_name":"Communication"},"service_owner":{"id":281,"name":"Jo-Ann Stock","account":{"id":"widget","name":"Widget International"}},"source":null,"sourceID":null,"support_team":{"id":15,"name":"Windows Servers"},"updated_at":"2017-05-29T13:46:44-05:00","localized_description":"The Email service provides the ability to send email messages to, and receive emails from, email users within the organization and email users connected to the internet.","localized_name":"Email"}
```

The response contains [these fields](../services.html#fields).

## Create a service

```
POST /services
```

When creating a new service [these fields](../services.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"availability_manager":"...","...":"..."}
```

The response contains [all fields](../services.html#fields) of the created service and is similar to the response in [Get a single service](../services.html#get-a-single-service)

## Update a service

```
PATCH /services/:id
```

When updating a service [these fields](../services.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"availability_manager":"...","...":"..."}
```

The response contains [all fields](../services.html#fields) of the updated service and is similar to the response in [Get a single service](../services.html#get-a-single-service)

## Fields

attachments
: *Readonly* **aggregated Attachments**

availability\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Availability manager field is used to select the person who is responsible for ensuring that the availability targets specified in the active SLAs for the service are met.

capacity\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Capacity manager field is used to select the person who is responsible for ensuring that the service is not affected by incidents that are caused by capacity shortages.

change\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Change manager field is used to select the person who is responsible for coordinating the changes of the service.

continuity\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Continuity manager field is used to select the person who is responsible for creating and maintaining the continuity plans for the service’s instances that have an active SLA with a continuity target.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the service was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the service.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to enter a high-level description of the service’s core functionality.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the service may no longer be related to other records.

first\_line\_team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The First line team field is used to select the [team](../teams.html) that will, by default, be selected in the First line team field of a new [service instance](../service_instances/index.html) when it is being registered for the service.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the service.

impact
: *Readonly* **[enum](../general/enumerations/index.html)** — The Impact field shows the impact based on the highest impact of the affected SLAs for which the current user has read access. Valid values are:
: - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

keywords
: *Optional* **[string](../general/data_types.html) (max 2048)** — The Keywords field contains a comma-separated list of words that can be used to find the service via search.

knowledge\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Knowledge manager field is used to select the person who is responsible for the quality of the [knowledge articles](../knowledge_articles.html) for the service.

localized\_description
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — Translated Description in the current [language](../index.html#internationalization), defaults to `description` in case no translation is provided.

localized\_keywords
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — Translated Keywords in the current [language](../index.html#internationalization), defaults to `keywords` in case no translation is provided.

localized\_name
: *Readonly* **[string](../general/data_types.html) (max 80)** — Translated Name in the current [language](../index.html#internationalization), defaults to `name` in case no translation is provided.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the service. The service name may be followed by the name of its core application placed between brackets.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the service. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

problem\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Problem manager field is used to select the person who is responsible for coordinating the problems that directly affect the service.

provider
: *Required* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)**

release\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Release manager field is used to select the person who is responsible for coordinating the releases of the service.

service\_owner
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Service owner field is used to select the [Person](../people.html) who is responsible for ensuring that the service level targets specified in the SLAs for the service are met.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

support\_team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Support team field is used to select the [team](../teams.html) that will, by default, be selected in the Support team field of a [service instance](../service_instances/index.html) when one is registered for the service. Similarly, this team will be selected in the Team field of a [Problem](../problems.html) when the service is related to it.

survey
: *Optional* **[reference](../general/data_types.html#references) to [Survey](../surveys.html)** — The Survey field is used to select the [survey](../surveys.html) that will be presented to users to give their rating for this service.

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the service.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the service. If the service has no updates it contains the `created_at` value.
