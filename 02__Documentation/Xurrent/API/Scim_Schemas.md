# SCIM Schemas API

- [List schemas](../schemas.html#list-schemas)
- [Get the user schema](../schemas.html#get-the-user-schema)
- [Get the enterprise user schema](../schemas.html#get-the-enterprise-user-schema)
- [Get the group schema](../schemas.html#get-the-group-schema)
- [List response fields](../schemas.html#list-response-fields)
- [Fields](../schemas.html#fields)

## List schemas

```
GET /scim/v2/Schemas
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:api:messages:2.0:ListResponse"],"totalResults":3,"itemsPerPage":3,"startIndex":1,"Resources":[{"id":"urn:ietf:params:scim:schemas:core:2.0:User","name":"User","description":"User Schema","attributes":["..."],"meta":{"resourceType":"Schema","location":"https://wdc.test.host/scim/v2/Schemas/urn:ietf:params:scim:schemas:core:2.0:User"}},{"id":"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User","name":"Enterprise User","description":"Enterprise User Schema","attributes":["..."],"meta":{"resourceType":"Schema","location":"https://wdc.test.host/scim/v2/Schemas/urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"}},{"id":"urn:ietf:params:scim:schemas:core:2.0:Group","name":"Group","description":"Group Schema","attributes":["..."],"meta":{"resourceType":"Schema","location":"https://wdc.test.host/scim/v2/Schemas/urn:ietf:params:scim:schemas:core:2.0:Group"}}]}
```

The response contains [these fields](../schemas.html#list-response-fields).

## Get the user schema

```
GET /scim/v2/Schemas/urn:ietf:params:scim:schemas:core:2.0:User
```

### Response

Based on [RFC 7643 User Resource Schema](https://tools.ietf.org/html/rfc7643#section-4.1).

```
status: 200 OK
```

```
{"id":"urn:ietf:params:scim:schemas:core:2.0:User","name":"User","description":"User Schema","attributes":[{"name":"userName","type":"string","multiValued":false,"required":true,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"server","description":"Unique identifier for the User, typically used by the user to directly authenticate to the service provider. Each User MUST include a non-empty userName value. This identifier MUST be unique across the service provider's entire set of Users."},{"name":"name","type":"complex","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The components of the user's real name. Providers MAY return just the full name as a single string in the formatted sub-attribute, or they MAY return just the individual component attributes using the other sub-attributes, or they MAY return both. If both variants are returned, they SHOULD be describing the same name, with the formatted name indicating how the component attributes should be combined.","subAttributes":[{"name":"formatted","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The full name, including all middle names, titles, and suffixes as appropriate, formatted for display (e.g., 'Ms. Barbara J Jensen, III')."},{"name":"familyName","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The family name of the User, or last name in most Western languages (e.g., 'Jensen' given the full name 'Ms. Barbara J Jensen, III')."},{"name":"givenName","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The given name of the User, or first name in most Western languages (e.g., 'Barbara' given the full name 'Ms. Barbara J Jensen, III')."},{"name":"middleName","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The middle name(s) of the User (e.g., 'Jane' given the full name 'Ms. Barbara J Jensen, III')."},{"name":"honorificPrefix","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The honorific prefix(es) of the User, or title in most Western languages (e.g., 'Ms.' given the full name 'Ms. Barbara J Jensen, III')."},{"name":"honorificSuffix","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The honorific suffix(es) of the User, or suffix in most Western languages (e.g., 'III' given the full name 'Ms. Barbara J Jensen, III')."}]},{"name":"displayName","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The name of the User, suitable for display to end-users. The name SHOULD be the full name of the User being described, if known."},{"name":"nickName","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The casual way to address the user in real life, e.g., 'Bob' or 'Bobby' instead of 'Robert'. This attribute SHOULD NOT be used to represent a User's username (e.g., 'bjensen' or 'mpepperidge')."},{"name":"profileUrl","type":"reference","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","referenceTypes":["external"],"description":"A fully qualified URL pointing to a page representing the User's online profile."},{"name":"title","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The user's title, such as 'Vice President.'"},{"name":"userType","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Used to identify the relationship between the organization and the user. Typical values used might be 'Contractor', 'Employee', 'Intern', 'Temp', 'External', and 'Unknown', but any value may be used."},{"name":"preferredLanguage","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Indicates the User's preferred written or spoken language. Generally used for selecting a localized user interface; e.g., 'en_US' specifies the language English and country US."},{"name":"locale","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Used to indicate the User's default location for purposes of localizing items such as currency, date time format, or numerical representations."},{"name":"timezone","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The User's time zone in the 'Olson' time zone database format, e.g., 'America/Los_Angeles'."},{"name":"active","type":"boolean","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A Boolean value indicating the User's administrative status."},{"name":"password","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"writeOnly","returned":"never","uniqueness":"none","description":"The User's cleartext password. This attribute is intended to be used as a means to specify an initial password when creating a new User or to reset an existing User's password."},{"name":"emails","type":"complex","multiValued":true,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Email addresses for the user. The value SHOULD be canonicalized by the service provider, e.g., 'bjensen@example.com' instead of 'bjensen@EXAMPLE.COM'.","subAttributes":[{"name":"value","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Email addresses for the user. The value SHOULD be canonicalized by the service provider, e.g., 'bjensen@example.com' instead of 'bjensen@EXAMPLE.COM'."},{"name":"display","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A human-readable name, primarily used for display purposes."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","canonicalValues":["work","home","other"],"description":"A label indicating the attribute's function, e.g., 'work' or 'home'."},{"name":"primary","type":"boolean","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A Boolean value indicating the 'primary' or preferred attribute value for this attribute, e.g., the preferred mailing address or primary email address. The primary attribute value 'true' MUST appear no more than once."}]},{"name":"phoneNumbers","type":"complex","multiValued":true,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Phone numbers for the User. The value SHOULD be canonicalized by the service provider according to the format specified in RFC 3966, e.g., 'tel:+1-201-555-0123'.","subAttributes":[{"name":"value","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Phone number of the User."},{"name":"display","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A human-readable name, primarily used for display purposes."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","canonicalValues":["work","home","mobile","fax","pager","other"],"description":"A label indicating the attribute's function, e.g., 'work', 'home', 'mobile'."},{"name":"primary","type":"boolean","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A Boolean value indicating the 'primary' or preferred attribute value for this attribute, e.g., the preferred mailing address or primary email address. The primary attribute value 'true' MUST appear no more than once."}]},{"name":"ims","type":"complex","multiValued":true,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Instant messaging addresses for the User.","subAttributes":[{"name":"value","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Instant messaging address for the User."},{"name":"display","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A human-readable name, primarily used for display purposes."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","canonicalValues":["aim","gtalk","icq","xmpp","msn","skype","qq","yahoo"],"description":"A label indicating the attribute's function, e.g., 'aim', 'gtalk', 'xmpp'."},{"name":"primary","type":"boolean","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A Boolean value indicating the 'primary' or preferred attribute value for this attribute, e.g., the preferred mailing address or primary email address. The primary attribute value 'true' MUST appear no more than once."}]},{"name":"photos","type":"complex","multiValued":true,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"URLs of photos of the User.","subAttributes":[{"name":"value","type":"reference","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","referenceTypes":["external"],"description":"URLs of a photo of the User."},{"name":"display","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A human-readable name, primarily used for display purposes."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","canonicalValues":["photo","thumbnail"],"description":"A label indicating the attribute's function, i.e., 'photo' or 'thumbnail'."},{"name":"primary","type":"boolean","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A Boolean value indicating the 'primary' or preferred attribute value for this attribute, e.g., the preferred mailing address or primary email address. The primary attribute value 'true' MUST appear no more than once."}]},{"name":"addresses","type":"complex","multiValued":true,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A physical mailing address for this User.","subAttributes":[{"name":"formatted","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The full mailing address, formatted for display or use with a mailing label. This attribute MAY contain newlines."},{"name":"streetAddress","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The full street address component, which may include house number, street name, P.O. box, and multi-line extended street address information. This attribute MAY contain newlines."},{"name":"locality","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The city or locality component."},{"name":"region","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The state or region component."},{"name":"postalCode","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The zip code or postal code component."},{"name":"country","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The country name component."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","canonicalValues":["work","home","other"],"description":"A label indicating the attribute's function, e.g., 'work' or 'home'."}]},{"name":"groups","type":"complex","multiValued":true,"required":false,"mutability":"readOnly","returned":"default","uniqueness":"none","description":"A list of groups to which the user belongs, either through direct membership, through nested groups, or dynamically calculated.","subAttributes":[{"name":"value","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readOnly","returned":"default","uniqueness":"none","description":"The identifier of the User's group."},{"name":"$ref","type":"reference","multiValued":false,"required":false,"caseExact":false,"mutability":"readOnly","returned":"default","uniqueness":"none","referenceTypes":["Group"],"description":"The URI of the corresponding 'Group' resource to which the user belongs."},{"name":"display","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readOnly","returned":"default","uniqueness":"none","description":"A human-readable name, primarily used for display purposes."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","canonicalValues":["direct","indirect"],"description":"A label indicating the attribute's function, e.g., 'direct' or 'indirect'."}]},{"name":"entitlements","type":"complex","multiValued":true,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A list of entitlements for the User that represent a thing the User has.","subAttributes":[{"name":"value","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The value of an entitlement."},{"name":"display","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A human-readable name, primarily used for display purposes."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A label indicating the attribute's function."},{"name":"primary","type":"boolean","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A Boolean value indicating the 'primary' or preferred attribute value for this attribute, e.g., the preferred mailing address or primary email address. The primary attribute value 'true' MUST appear no more than once."}]},{"name":"roles","type":"complex","multiValued":true,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A list of roles for the User that collectively represent who the User is, e.g., 'Student', 'Faculty'.","subAttributes":[{"name":"value","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The value of a role."},{"name":"display","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A human-readable name, primarily used for display purposes."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A label indicating the attribute's function."},{"name":"primary","type":"boolean","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A Boolean value indicating the 'primary' or preferred attribute value for this attribute, e.g., the preferred mailing address or primary email address. The primary attribute value 'true' MUST appear no more than once."}]},{"name":"x509Certificates","type":"complex","multiValued":true,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A list of certificates issued to the User.","subAttributes":[{"name":"value","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The value of an X.509 certificate."},{"name":"display","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A human-readable name, primarily used for display purposes."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A label indicating the attribute's function."},{"name":"primary","type":"boolean","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A Boolean value indicating the 'primary' or preferred attribute value for this attribute, e.g., the preferred mailing address or primary email address. The primary attribute value 'true' MUST appear no more than once."}]}],"meta":{"resourceType":"Schema","location":"https://wdc.test.host/scim/v2/Schemas/urn:ietf:params:scim:schemas:core:2.0:User"}}
```

The response contains [these fields](../schemas.html#fields)

## Get the enterprise user schema

```
GET /scim/v2/Schemas/urn:ietf:params:scim:schemas:extension:enterprise:2.0:User
```

### Response

Based on [RFC 7643 Enterprise User Extension Resource Schema](https://tools.ietf.org/html/rfc7643#section-4.3).

```
status: 200 OK
```

```
{"id":"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User","name":"Enterprise User","description":"Enterprise User Schema","attributes":[{"name":"employeeNumber","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Numeric or alphanumeric identifier assigned to a person, typically based on order of hire or association with an organization."},{"name":"costCenter","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Identifies the name of a cost center."},{"name":"organization","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Identifies the name of an organization."},{"name":"division","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Identifies the name of a division."},{"name":"department","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Identifies the name of a department."},{"name":"manager","type":"complex","multiValued":false,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The User's manager. A complex type that optionally allows service providers to represent organizational hierarchy by referencing the 'id' attribute of another User.","subAttributes":[{"name":"value","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"The id of the SCIM resource representing the User's manager."},{"name":"$ref","type":"reference","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","referenceTypes":["User"],"description":"The URI of the SCIM resource representing the User's manager."},{"name":"displayName","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readOnly","returned":"default","uniqueness":"none","description":"The displayName of the User's manager."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","canonicalValues":["direct","indirect"],"description":"A label indicating the attribute's function, e.g., 'direct' or 'indirect'."}]},{"name":"site","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Identifies the name of a site."},{"name":"location","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Identifies the name of the location, e.g. Room 12."}],"meta":{"resourceType":"Schema","location":"https://wdc.test.host/scim/v2/Schemas/urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"}}
```

The response contains [these fields](../schemas.html#fields).

## Get the group schema

```
GET /scim/v2/Schemas/urn:ietf:params:scim:schemas:core:2.0:Group
```

### Response

Based on [RFC 7643 Group Resource Schema](https://tools.ietf.org/html/rfc7643#section-4.2).

```
status: 200 OK
```

```
{"id":"urn:ietf:params:scim:schemas:core:2.0:Group","name":"Group","description":"Group Schema","attributes":[{"name":"displayName","type":"string","multiValued":false,"required":true,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"server","description":"A human-readable name for the Group."},{"name":"groupType","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"Used to identify the relationship between the organization and the group. Typical values used might be 'Organization', 'Site', 'Team', but any value may be used."},{"name":"members","type":"complex","multiValued":true,"required":false,"mutability":"readWrite","returned":"default","uniqueness":"none","description":"A list of members of the Group.","subAttributes":[{"name":"value","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"immutable","returned":"default","uniqueness":"none","description":"Identifier of the member of this Group."},{"name":"$ref","type":"reference","multiValued":false,"required":false,"caseExact":false,"mutability":"immutable","returned":"default","uniqueness":"none","referenceTypes":["Group","User"],"description":"The URI corresponding to a SCIM resource that is a member of this Group."},{"name":"type","type":"string","multiValued":false,"required":false,"caseExact":false,"mutability":"immutable","returned":"default","uniqueness":"none","canonicalValues":["Group","User"],"description":"A label indicating the type of resource, e.g., 'User' or 'Group'."}]}],"meta":{"resourceType":"Schema","location":"https://wdc.test.host/scim/v2/Schemas/urn:ietf:params:scim:schemas:core:2.0:Group"}}
```

The response contains [these fields](../schemas.html#fields)

## List response fields

Definitions taken from [RFC 7644 - List Response](https://tools.ietf.org/html/rfc7644#section-3.4.2)

totalResults
: *Readonly* **[integer]** — The number of results.

itemsPerPage
: *Readonly* **[integer]** — The number of results per page.

startIndex
: *Readonly* **[integer]** — The offset, or the number of results skipped.

Resources
: *Readonly* **[array]** — A multi-valued list of complex objects containing the requested resources containing [these fields](../schemas.html#fields).

## Fields

Definitions taken from [RFC 7643 - Schema Definition](https://tools.ietf.org/html/rfc7643#section-7)

id
: *Readonly* **[string]** — The unique URI of the schema.

name
: *Readonly* **[string]** — The schema’s human-readable name.

description
: *Readonly* **[string]** — The schema’s human-readable description.

attributes
: *Readonly* **[array]** — A complex type that defines service provider attributes and their qualities.

attributes.name
: *Readonly* **[string]** — The attribute’s name.

attributes.type
: *Readonly* **[string]** — The attribute’s data type. Valid values are `string`, `boolean`, `decimal`, `integer`, `dateTime`, `reference`, and `complex`.

attributes.subAttributes
: *Readonly* **[string]** — When an attribute is of type `complex`, `subAttributes` defines a set of sub-attributes. `subAttributes` has the same schema sub-attributes as `attributes`.

attributes.description
: *Readonly* **[string]** — The attribute’s human-readable description.

attributes.required
: *Readonly* **[boolean]** — Whether or not the attribute is required.

attributes.canonicalValues
: *Readonly* **[string]** — A collection of suggested canonical values that may be used (e.g., `work` and `home`).

attributes.caseExact
: *Readonly* **[boolean]** — Whether or not a string attribute is case sensitive.

attributes.mutability
: *Readonly* **[string]**, default: `readWrite` — A single keyword indicating the circumstances under which the value of the attribute can be (re)defined. Valid values are:
: - `readOnly`: The attribute shall not be modified.
 - `readWrite`: The attribute may be updated and read at any time.
 - `immutable`: The attribute may be defined at resource creation (e.g., POST) or at record replacement via a request (e.g., a PUT). The attribute shall not be updated.
 - `writeOnly`: The attribute may be updated at any time. Attribute values shall not be returned (e.g., because the value is a stored hash).

attributes.returned
: *Readonly* **[string]**, default: `always` — A single keyword that indicates when an attribute and associated values are returned in response to a GET request or in response to a PUT, POST, or PATCH request. Valid values are:
: - `always`: The attribute is always returned, regardless of the contents of the `attributes` parameter. For example, `id` is always returned to identify a SCIM resource.
 - `never`: The attribute is never returned.
 - `default`: The attribute is returned by default in all SCIM operation responses where attribute values are returned.
 - `request`: The attribute is returned in response to any PUT, POST, or PATCH operations if the attribute was specified by the client (for example, the attribute was modified).

attributes.uniqueness
: *Readonly* **[string]**, default: `none` — A single keyword value that specifies how the service provider enforces uniqueness of attribute values. Valid values are:
: - `none`: The values are not intended to be unique in any way.
 - `server`: The value should be unique within the context of the service provider (SCIM endpoint) and may be globally unique.
 - `global`: The value should be globally unique (e.g. a GUID). No two resources on any server should possess the same value.

attributes.referenceTypes
: *Readonly* **[array]** — A multi-valued array of JSON strings that indicate the SCIM resource types that may be referenced. Valid values are:
: - `...`: Any SCIM resource type.
 - `external`: Reference to an external resource (e.g., a photo)
 - `uri`: Reference to a service endpoint or an identifier (e.g., a schema URN).

meta.location
: *Readonly* **[string]** — The URI of this schema.

meta.resourceType
: *Readonly* **[string]** — The name of this schema.
