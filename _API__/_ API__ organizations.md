# Organizations API

- [List organizations](../organizations.html#list-organizations)
- [Get a single organization](../organizations.html#get-a-single-organization)
- [Create an organization](../organizations.html#create-a-organization)
- [Update an organization](../organizations.html#update-a-organization)
- [Fields](../organizations.html#fields)

## List organizations

List all organizations for an account:

```
GET /organizations
```

### Response

```
status: 200 OK
```

```
[{"id":44,"sourceID":null,"name":"Widget Data Center, External IT","parent":{"id":6,"name":"Widget Data Center"},"manager":{"id":6,"name":"Howard Tanner"},"created_at":"2016-03-22T21:02:50-05:00","updated_at":"2016-03-25T16:54:52-05:00"},{"id":50,"sourceID":null,"name":"Widget North America, Finance","parent":{"id":51,"name":"Widget North America, Inc."},"manager":{"id":120,"name":"Carolyn Goldrat"},"created_at":"2016-03-22T21:02:50-05:00","updated_at":"2016-03-22T21:03:36-05:00"},"..."]
```

The response contains [these fields](../organizations.html#collection-fields) by default. [Filtering](../organizations.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of organizations.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/organizations/disabled`: List all disabled organizations
- `/organizations/enabled`: List all enabled organizations
- `/organizations/external`: List all external organizations
- `/organizations/internal`: List all internal organizations
- `/organizations/trusted`: List all trusted organizations
- `/organizations/directory`: List all organizations registered in the directory account of the support domain account from which the data is requested
- `/organizations/support_domain`: List all organizations registered in the account from which the data is requested
- `/organizations/managed_by_me`: List all organizations which manager or substitute is the API user

### Collection Fields

By default the following [fields](../organizations.html#fields) will appear in collections of organizations:

`id` `sourceID` `name` `parent` `manager` `created_at` `updated_at`

Obtain a different set of [fields](../organizations.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../organizations.html#fields):

`id` `source` `sourceID` `name` `disabled` `created_at` `updated_at` `disabled` `financialID` `parent`

### Sorting

By default a collection of organizations is sorted **ascending** by `name`.

The following [fields](../organizations.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

### Response

The response is similar to the response in [List organizations](../organizations.html#list-organizations)

## Get a single organization

```
GET /organizations/:id
```

### Response

```
status: 200 OK
```

```
{"addresses":[{"address":"1172 Park Avenue","city":"New York","country":"US","id":71,"integration":false,"label":"street","state":"NY","zip":"10128"}],"business_unit":false,"business_unit_organization":{"id":51,"name":"Widget North America, Inc."},"contacts":[{"id":225,"label":"general","telephone":"+1 (212) 369 2610"},{"id":226,"label":"fax","telephone":"+1 (212) 369 2611"},{"id":227,"label":"general","website":"www.widget.com"}],"created_at":"2016-03-22T21:02:50-05:00","custom_fields":null,"disabled":false,"id":50,"manager":{"id":120,"name":"Carolyn Goldrat"},"name":"Widget North America, Finance","parent":{"id":51,"name":"Widget North America, Inc."},"picture_uri":null,"region":"NA","remarks":"The Finance department of Widget North America, Inc. is responsible for purchasing, accounting, and invoicing within Widget North America, Inc.","source":null,"sourceID":null,"substitute":{"id":121,"name":"Buck Kreuter"},"ui_extension":null,"updated_at":"2016-03-22T21:03:36-05:00"}
```

The response contains [these fields](../organizations.html#fields).

## Create an organization

```
POST /organizations
```

When creating an organization [these fields](../organizations.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"addresses":"...","...":"..."}
```

The response contains [all fields](../organizations.html#fields) of the created organization and is similar to the response in [Get a single organization](../organizations.html#get-a-single-organization)

## Update an organization

```
PATCH /organizations/:id
```

When updating an organization [these fields](../organizations.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"addresses":"...","...":"..."}
```

The response contains [all fields](../organizations.html#fields) of the updated organization and is similar to the response in [Get a single organization](../organizations.html#get-a-single-organization)

## Fields

addresses
: *Readonly* **aggregated [Addresses](addresses/index.html)** — The Address fields are used to enter the street, mailing and billing addresses of the organization.

attachments
: *Readonly* **aggregated Attachments**

business\_unit
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Business unit box is checked when the organization needs to be treated as a separate entity from a reporting perspective. This checkbox is only available for internal organizations.

business\_unit\_organization
: *Readonly* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — Refers to itself if the organization is a business unit, or refers to the business unit that the organization belongs to.

contacts
: *Readonly* **aggregated [Contacts](contacts/index.html)** — The Contact fields are used to enter the general/service desk email addresses, general/fax/etc. of the organization.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the organization was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the organization.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the organization may no longer be related to other records.

end\_user\_privacy
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The End user privacy box is checked when end users from this organization should be prevented from seeing information of other end users.

financialID
: *Optional* **[string](../general/data_types.html) (max 128)** — The Financial ID field is used to enter the unique identifier by which the organization is known in the financial system.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the organization.

manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field is used to select the manager of the organization.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the full name of the organization.

order\_template
: *Required* **[reference](../general/data_types.html#references) to [Request template](../request_templates.html)** — Refers to the order template that is used for purchases of people defined in this organization or its descendants.

parent
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Parent organization field is used to select the organization’s parent organization.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the organization. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

region
: *Optional* **[string](../general/data_types.html) (max 128)** — The Region field is used to specify which region the organization belongs to. It is possible to select a previously entered region name or to enter a new one. This field is only available when the organization is a business unit (i.e. when the Business unit box is checked). Although not visible, the Region field of a business unit’s child organizations is automatically set to the same value as the Region field of the business unit.
 Examples of commonly used region names are:
: - Asia Pacific (APAC)
 - Europe, Middle East & Africa (EMEA)
 - North America (NA)

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the organization that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Remarks field.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

substitute
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Substitute field is used to select the person who acts as the substitute of the organization’s manager.

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the organization.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the organization. If the organization has no updates it contains the `created_at` value.
