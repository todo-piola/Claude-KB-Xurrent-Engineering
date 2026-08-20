# SCIM Resource Types API

- [List resource types](index.html#list-resource-types)
- [Get the user resource type](index.html#get-the-user-resource-type)
- [Get the group resource type](index.html#get-the-group-resource-type)
- [List response fields](index.html#list-response-fields)
- [Fields](index.html#fields)

## List resource types

```
GET /scim/v2/ResourceTypes
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:api:messages:2.0:ListResponse"],"totalResults":2,"itemsPerPage":2,"startIndex":1,"Resources":[{"schemas":["urn:ietf:params:scim:schemas:core:2.0:ResourceType"],"id":"User","name":"User","endpoint":"/Users","description":"https://tools.ietf.org/html/rfc7643#section-8.7.1","schema":"urn:ietf:params:scim:schemas:core:2.0:User","schemaExtensions":[{"schema":"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User","required":false}],"meta":{"location":"https://<account>.xurrent.com/scim/v2/ResourceTypes/User","resourceType":"ResourceType"}},{"schemas":["urn:ietf:params:scim:schemas:core:2.0:ResourceType"],"id":"Group","name":"Group","endpoint":"/Groups","description":"https://tools.ietf.org/html/rfc7643#section-8.7.1","schema":"urn:ietf:params:scim:schemas:core:2.0:Group","meta":{"location":"https://<account>.xurrent.com/scim/v2/ResourceTypes/Group","resourceType":"ResourceType"}}]}
```

The response contains [these fields](index.html#list-response-fields).

## Get the User Resource Type

```
GET /scim/v2/ResourceTypes/User
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:schemas:core:2.0:ResourceType"],"id":"User","name":"User","endpoint":"/Users","description":"https://tools.ietf.org/html/rfc7643#section-8.7.1","schema":"urn:ietf:params:scim:schemas:core:2.0:User","schemaExtensions":[{"schema":"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User","required":false}],"meta":{"location":"https://<account>.xurrent.com/scim/v2/ResourceTypes/User","resourceType":"ResourceType"}}
```

The response contains [these fields](index.html#fields).

## Get the group resource type

```
GET /scim/v2/ResourceTypes/Group
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:schemas:core:2.0:ResourceType"],"id":"Group","name":"Group","endpoint":"/Groups","description":"https://tools.ietf.org/html/rfc7643#section-8.7.1","schema":"urn:ietf:params:scim:schemas:core:2.0:Group","meta":{"location":"https://<account>.xurrent.com/scim/v2/ResourceTypes/Group","resourceType":"ResourceType"}}
```

The response contains [these fields](index.html#fields).

## List response fields

Definitions taken from [RFC 7644 - List Response](https://tools.ietf.org/html/rfc7644#section-3.4.2)

totalResults
: *Readonly* **[integer]** — The number of results.

itemsPerPage
: *Readonly* **[integer]** — The number of results per page.

startIndex
: *Readonly* **[integer]** — The offset, or the number of results skipped.

Resources
: *Readonly* **[array]** — A multi-valued list of complex objects containing the requested resources containing [these fields](index.html#fields).

## Fields

Definitions taken from [RFC 7643 - Resource Type Schema](https://tools.ietf.org/html/rfc7643#section-6)

id
: *Readonly* **[string]** — The resource type’s unique id.

name
: *Readonly* **[string]** — The resource type name.

description
: *Readonly* **[string]** — The resource type’s human-readable description.

endpoint
: *Readonly* **[string]** — The resource type’s HTTP-addressable endpoint relative to the Base URL of the service provider, e.g., “Users”.

schema
: *Readonly* **[string]** — The resource type’s primary/base schema URI, e.g., “urn:ietf:params:scim:schemas:core:2.0:User”.

schemaExtensions
: *Readonly* **[array]** — A list of URIs of the resource type’s schema extensions.

schemaExtensions.schema
: *Readonly* **[string]** — The URI of an extended schema, e.g., “urn:ietf:params:scim:schemas:extension:enterprise:2.0:User”.

schemaExtensions.required
: *Readonly* **[boolean]** — Whether or not the schema extension is required for the resource type.

meta.location
: *Readonly* **[string]** — The URI of this resource type.

meta.resourceType
: *Readonly* **[string]** — The name of the resource type.
