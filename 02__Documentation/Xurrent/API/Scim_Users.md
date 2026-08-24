# SCIM Users API

- [List users](../users.html#list-users)
 - [Pagination](../users.html#pagination)
 - [Filtering](../users.html#filtering)
- [Get a single user](../users.html#get-a-single-user)
- [Create a user](../users.html#create-a-user)
- [Update a user](../users.html#update-a-user)
- [Delete a user](../users.html#delete-a-user)
- [List response fields](../users.html#list-response-fields)
- [Fields](../users.html#fields)
- [Enterprise extension fields](../users.html#enterprise-extension-fields)
- [Custom fields extension](../users.html#custom-fields-extension)

## List users

```
GET /scim/v2/Users
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:api:messages:2.0:ListResponse"],"totalResults":2,"itemsPerPage":25,"startIndex":1,"Resources":[{"schemas":["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"],"id":"2","externalId":"SCIM1","userName":"Jane Doe","meta":{"resourceType":"User","created":"2018-04-17T09:03:39-05:00","lastModified":"2018-04-17T09:03:39-05:00","location":"https://<account>.xurrent.com/scim/v2/Users/2"},"name":{"familyName":"Doe","givenName":"Jane","middleName":"","honorificPrefix":"Mrs","honorificSuffix":"MD","formatted":"Mrs Jane Doe MD"},"displayName":"Jane Doe","nickName":"Nick Jane","profileUrl":"http://skimmer.com/jane","title":"First Class Skimmer","...":"..."},{"schemas":["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"],"id":"1","externalId":"SCIM2","userName":"Card Skimmer","meta":{"resourceType":"User","created":"2018-04-17T09:03:12-05:00","lastModified":"2018-04-17T09:03:12-05:00","location":"https://<account>.xurrent.com/scim/v2/Users/1"},"name":{"familyName":"Skimmer","givenName":"Card","middleName":"","honorificPrefix":"Sir","honorificSuffix":"MD","formatted":"Sir Card Skimmer MD"},"displayName":"Card Skimmer","nickName":"Nicked Name","...":"..."}]}
```

The response contains [these fields](../users.html#list-response-fields).

### Pagination

The SCIM Users API supports filtering as defined in [RFC 7644 - Pagination](https://tools.ietf.org/html/rfc7644#section-3.4.2.4)

startIndex
: **[integer]**, default: `1` — The 1-based index of the first query result.

count
: **[integer]**, default: `25` — Non-negative integer between 1 and 25 indicating the desired maximum number of results per page, e.g., 10.

Examples:

```
GET /scim/v2/Users?startIndex=10&count=10
```

### Filtering

The SCIM Users API partially supports filtering as defined in [RFC 7644 - Filtering](https://tools.ietf.org/html/rfc7644#section-3.4.2.2)

Filtering is available for the following attributes:
: - `userName`
 - `externalId`
 - `active`
 - `meta.lastModified`
 - `meta.created`

The following operators are available:
: - `eq` Equal to
 - `ne` Not equal to
 - `lt` Less than
 - `gt` Greater than

The logical operators `and` and `or` are also supported.

Examples:

```
GET /scim/v2/Users?filter=userName eq "jane.doe@scim.com"
GET /scim/v2/Users?filter=userName ne "card.skimmer@scim.com"
GET /scim/v2/Users?filter=externalId eq "SCIM1"
GET /scim/v2/Users?filter=active eq "true"
GET /scim/v2/Users?filter=active ne "true"
GET /scim/v2/Users?filter=meta.lastModified lt "2018-04-19T13:47:13Z"
GET /scim/v2/Users?filter=meta.created gt "2018-04-19T13:47:13Z"
GET /scim/v2/Users?filter=meta.lastModified gt "2018-04-19T13:47:13Z" and userName eq "jane.doe@scim.com"
GET /scim/v2/Users?filter=userName eq "card.skimmer@scim.com or userName eq "jane.doe@scim.com"
```

## Get a single user

```
GET /scim/v2/Users/:id
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"],"id":"2","externalId":"SCIM1","userName":"Jane Doe","meta":{"resourceType":"User","created":"2018-04-17T09:03:39-05:00","lastModified":"2018-04-17T09:03:39-05:00","location":"https://<account>.xurrent.com/scim/v2/Users/2"},"name":{"familyName":"Doe","givenName":"Jane","middleName":"","honorificPrefix":"Mrs","honorificSuffix":"MD","formatted":"Mrs Jane Doe MD"},"displayName":"Jane Doe","nickName":"Nick Jane","profileUrl":"http://skimmer.com/jane","title":"First Class Skimmer","userType":"Skimmer","preferredLanguage":"Dutch","locale":"nl","timezone":"Amsterdam","active":true,"emails":[{"type":"work","value":"jane.doe@scim.com","primary":true},{"type":"personal","value":"private.skimmer@example.com"}],"phoneNumbers":[{"type":"work","value":"+31 65 7777777","primary":true},{"type":"personal","value":"+31 20 4444444"}],"ims":[{"type":"twitter","value":"newt"}],"photos":[{"value":"photo1"}],"addresses":[{"type":"work","streetAddress":"Banklaan 1","locality":"Amsterdam","region":"Noord Holland","postalCode":"1000 AA","country":"Netherlands","primary":true}],"entitlements":[{"value":"one"},{"value":"two"},{"value":"three"}],"roles":[{"value":"specialist"},{"value":"workflow_manager"},{"value":"service_manager"}],"x509Certificates":[{"value":"MIIDQzCCAqyg\nEzARBgNVBAg\n0xMjEwMDQwNjI0MzFa"}],"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User":{"employeeNumber":"555111","costCenter":"NL","organization":"Skim Holland","division":"5/0","department":"Skim Club","manager":{"displayName":"Card Skimmer","value":"1","$ref":"https://<account>.xurrent.com/scim/v2/Users/1"},"site":"Amsterdam","location":"Room 42"}}
```

The response contains [these fields](../users.html#fields).

## Create a user

```
POST /scim/v2/Users
```

When creating a new user [these fields](../users.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"schemas":["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"],"id":"5","...":"..."}
```

The response contains [all fields](../users.html#fields) of the created user and is similar to the response in [Get a single user](../users.html#get-a-single-user)

## Update a user

Xurrent accepts both `PUT` and `PATCH` HTTP methods. However in both cases Xurrent will only update the fields that are provided. To clear a field the caller must provide the field with the appropriate empty value.

```
PUT /scim/v2/Users/:id
PATCH /scim/v2/Users/:id
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"],"id":"5","...":"..."}
```

The response contains [all fields](../users.html#fields) of the created user and is similar to the response in [Get a single user](../users.html#get-a-single-user)

## Delete a user

SCIM users are never really deleted in Xurrent, instead the `active` attribute of the SCIM user will be set to `false` and the related Xurrent person record will be disabled.

```
DELETE /scim/v2/Users/:id
```

### Response

```
status: 204 No Content
```

## List response fields

Definitions taken from [RFC 7644 - List Response](https://tools.ietf.org/html/rfc7644#section-3.4.2)

totalResults
: *Readonly* **[integer]** — The number of results.

itemsPerPage
: *Readonly* **[integer]** — The number of results per page.

startIndex
: *Readonly* **[integer]** — The offset, or the number of results skipped.

Resources
: *Readonly* **[array]** — A multi-valued list of complex objects containing the requested resources containing [these fields](../users.html#fields).

## Fields

As defined in the [User Schema](../schemas.html#get-the-user-schema)

userName
: **[string]** — Unique identifier for the User, typically used by the user to directly authenticate to the service provider. Each User must include a non-empty userName value. This identifier must be unique across the service provider’s entire set of users.

name
: **[hash]** — The components of the user’s real name.

 name.formatted
 : **[string]** — The full name, including all middle names, titles, and suffixes as appropriate, formatted for display (e.g., ‘Ms. Barbara J Jensen, III’).

 name.familyName
 : **[string]** — The family name of the User, or last name in most Western languages (e.g., ‘Jensen’ given the full name ‘Ms. Barbara J Jensen, III’).

 name.givenName
 : **[string]** — The given name of the User, or first name in most Western languages (e.g., ‘Barbara’ given the full name ‘Ms. Barbara J Jensen, III’).

 name.middleName
 : **[string]** — The middle name(s) of the User (e.g., ‘Jane’ given the full name ‘Ms. Barbara J Jensen, III’).

 name.honorificPrefix
 : **[string]** — The honorific prefix(es) of the User, or title in most Western languages (e.g., ‘Ms.’ given the full name ‘Ms. Barbara J Jensen, III’).

 name.honorificSuffix
 : **[string]** — The honorific suffix(es) of the User, or suffix in most Western languages (e.g., ‘III’ given the full name ‘Ms. Barbara J Jensen, III’).

displayName
: **[string]** — The name of the User, suitable for display to end-users. The name should be the full name of the User being described, if known.”

nickName
: **[string]** — The casual way to address the user in real life, e.g., ‘Bob’ or ‘Bobby’ instead of ‘Robert’.

profileUrl
: **[uri]** — A fully qualified URL pointing to a page representing the User’s online profile.

title
: **[string]** — The user’s title, such as ‘Vice President’.

userType
: **[string]** — Used to identify the relationship between the organization and the user. Typical values used might be ‘Contractor’, ‘Employee’, ‘Intern’, ‘Temp’, ‘External’, and ‘Unknown’, but any value may be used.

preferredLanguage
: **[string]** — Indicates the User’s preferred written or spoken language. Generally used for selecting a localized user interface; e.g., ‘en\_US’ specifies the language English and country US.

locale
: **[string]** — Used to indicate the User’s default location for purposes of localizing items such as currency, date time format, or numerical representations.

timezone
: **[string]** — The User’s time zone in the ‘Olson’ time zone database format, e.g., ‘America/Los\_Angeles’.”

active
: **[boolean]** — Indicates the User’s administrative status.

password
: **[string]** — The User’s clear text password. **ignored by xurrent**

emails
: **[array]** — List of email addresses for the user.

 emails.value
 : **[string]** — Email addresses for the user.

 emails.display
 : **[string]** — A human-readable name, primarily used for display purposes.

 emails.type
 : **[string]** — Valid values `work`, `home` and `other`.

 emails.primary
 : **[boolean]** — Whether or not this is the primary email address.

phoneNumbers
: **[array]** — List of phone numbers for the user.

 phoneNumbers.value
 : **[string]** — Phone number of the User.

 phoneNumbers.display
 : **[string]** — A human-readable name, primarily used for display purposes.

 phoneNumbers.type
 : **[string]** — Valid values `work`, `home`, `mobile`, `fax`, `pager` and `other`.

 phoneNumbers.primary
 : **[boolean]** — Whether or not this is the primary phone number.

ims
: **[array]** — Instant messaging addresses for the user.

 ims.value
 : **[string]** — Instant messaging address of the User.

 ims.display
 : **[string]** — A human-readable name, primarily used for display purposes.

 ims.type
 : **[string]** — Valid values `aim`, `qtalk`, `icq`, `xmpp`, `msn`, `skype`, `qq` and `yahoo`.

 ims.primary
 : **[boolean]** — Whether or not this is the primary instant messaging address.

photos
: **[array]** — URLs of photos of the User.

 photos.value
 : **[string]** — URLs of photo of the User.

 photos.display
 : **[string]** — A human-readable name, primarily used for display purposes.

 photos.type
 : **[string]** — Valid values `photo` and `thumbnail`.

 photos.primary
 : **[boolean]** — Whether or not this is the primary photo.

addresses
: **[array]** — Physical mailing addresses for this User.

 addresses.formatted
 : **[string]** — The full mailing address, formatted for display or use with a mailing label.

 addresses.streetAddress
 : **[string]** — The full street address component, which may include house number, street name, P.O. box, and multi-line extended street address information.

 addresses.locality
 : **[string]** — The city or locality component.

 addresses.region
 : **[string]** — The state or region component.

 addresses.postalCode
 : **[string]** — The zip code or postal code component.

 addresses.country
 : **[string]** — The country name component.

 addresses.type
 : **[string]** — Valid values `work`, `home` and `other`.

groups
: *Readonly* **[array]** — A list of groups to which the user belongs, either through direct membership, through nested groups, or dynamically calculated.

 groups.value
 : *Readonly* **[string]** — The identifier of the User’s group.

 groups.$ref
 : *Readonly* **[uri]** — The URI of the corresponding ‘Group’ resource to which the user belongs.

 groups.display
 : *Readonly* **[string]** — A human-readable name, primarily used for display purposes.

 groups.type
 : *Readonly* **[string]** — A label indicating the attribute’s function, e.g., ‘direct’ or ‘indirect’.

entitlements
: **[array]** — A list of entitlements for the User that represent a thing the User has.

 entitlements.value
 : **[string]** — The value of an entitlement.

 entitlements.display
 : **[string]** — A human-readable name, primarily used for display purposes.

 entitlements.type
 : **[string]** — A label indicating the attribute’s function.

 entitlements.primary
 : **[boolean]** — Whether or not this is the primary entitlement.

roles
: **[array]** — A list of roles for the User that collectively represent who the User is, e.g., ‘workflow\_manager’, ‘service\_desk\_analyst’.

 roles.value
 : **[string]** — The value of a role.

 roles.display
 : **[string]** — A human-readable name, primarily used for display purposes.

 roles.type
 : **[string]** — A label indicating the attribute’s function.

 roles.primary
 : **[boolean]** — Whether or not this is the primary role.

x509Certificates
: **[array]** — : **[array]** — A list of certificates issued to the User.

 x509Certificates.value
 : **[string]** — The value of an X.509 certificate.

 x509Certificates.display
 : **[string]** — A human-readable name, primarily used for display purposes.

 x509Certificates.type
 : **[string]** — A label indicating the attribute’s function.

 x509Certificates.primary
 : **[boolean]** — Whether or not this is the primary certificate.

urn:ietf:params:scim:schemas:extension:enterprise:2.0:User
: **[hash]** — Enterprise User Schema extension fields, see [Enterprise extension fields](../users.html#enterprise-extension-fields)

meta.location
: **[string]** — The URI of this resource type.

meta.resourceType
: **[string]** — The name of the resource type.

## Enterprise extension fields

As defined in the [Enterprise User Schema](../schemas.html#get-the-enterprise-user-schema)

employeeNumber
: **[string]** — Numeric or alphanumeric identifier assigned to a person, typically based on order of hire or association with an organization.

costCenter
: **[string]** — Identifies the name of a cost center.

organization
: **[string]** — Identifies the name of an organization.

division
: **[string]** — Identifies the name of a division.

department
: **[string]** — Identifies the name of a department.

site
: **[string]** — **specific for xurrent** Identifies the name of a site.

location
: **[string]** — **specific for xurrent** Identifies the name of the location, e.g. Room 12.

manager
: **[hash]** — The User’s manager. A complex type that optionally allows service providers to represent organizational hierarchy by referencing the ‘id’ attribute of another User.

 manager.value
 : **[string]** — The id of the SCIM resource representing the User’s manager.

 manager.$ref
 : **[uri]** — The URI of the SCIM resource representing the User’s manager.

 manager.displayName
 : **[uri]** — The displayName of the User’s manager.

 manager.type
 : **[uri]** — A label indicating the attribute’s function, e.g., ‘direct’ or ‘indirect’.

supportID
: **[string]** — **specific for xurrent** Identifies the User’s support ID.

## Custom fields extension

To pass additional values from the Identity Provider to Xurrent the following schema extension is also supported:

```
urn:ietf:params:scim:schemas:extension:4me:1.0:custom_fields
```

Note that this Xurrent schema extension does not have to be added to the schemas definition. It will always be picked up in case the attribute mentioned above is present in the JSON hash.

A typical use case is:

```
{
 "schemas": [
 "urn:ietf:params:scim:schemas:core:2.0:User",
 "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
 ],
 "externalId": "d5d1a4c5-84bb-4883-8c2d-a12bf3676638",
 "userName": "john.doe@example.com",
 ...
 "urn:ietf:params:scim:schemas:extension:4me:1.0:custom_fields": {
 "payroll_id": "179e3587-8410-443b-95ff-b0e50a98b184",
 "year_of_birth": 1975
 }
}
```

If additional custom field properties are required and the Identity Provider allows more complex structures the following format is also supported:

```
{
 "schemas": [
 "urn:ietf:params:scim:schemas:core:2.0:User",
 "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
 ],
 "externalId": "d5d1a4c5-84bb-4883-8c2d-a12bf3676638",
 "userName": "john.doe@example.com",
 ...
 "urn:ietf:params:scim:schemas:extension:4me:1.0:custom_fields": {
 "custom_fields": [
 {"id": "payroll_id", "value": "179e3587-8410-443b-95ff-b0e50a98b184"},
 {"id": "year_of_birth", "value": 1975},
 ]
 }
}
```

Provided custom fields will be added to the `custom_fields` attribute in Xurrent and are accessible in automation rule expressions using:

```
payroll_id = custom_fields.payroll_id
```

To view the fields in the GUI a [UI Extension](../../ui_extensions.html) may be defined using the SCIM user category:

```
<div class="row vertical">
 <label for="payroll_id" title="Payroll ID">Payroll ID</label>
 <input id="payroll_id" type="text" autocomplete="off">
</div>

<div class="row vertical">
 <label for="year_of_birth" title="Year of birth">Year of birth</label>
 <input id="year_of_birth" type="number" autocomplete="off" min="1900" step="1">
</div>
```
