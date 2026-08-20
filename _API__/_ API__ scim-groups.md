# SCIM Groups API

- [List groups](../groups.html#list-groups)
 - [Pagination](../groups.html#pagination)
 - [Filtering](../groups.html#filtering)
- [Get a single group](../groups.html#get-a-single-group)
- [Create a group](../groups.html#create-a-group)
- [Update a group](../groups.html#update-a-group)
- [Delete a group](../groups.html#delete-a-group)
- [List response fields](../groups.html#list-response-fields)
- [Fields](../groups.html#fields)

## List group

```
GET /scim/v2/Groups
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:api:messages:2.0:ListResponse"],"totalResults":1,"itemsPerPage":25,"startIndex":1,"Resources":[{"schemas":["urn:ietf:params:scim:schemas:core:2.0:Group"],"id":"1","externalId":"G1","displayName":"Widget Data Center","groupType":"Organization","meta":{"resourceType":"Group","created":"2018-04-17T11:05:29-05:00","lastModified":"2018-04-17T11:05:29-05:00","location":"https://<account>.xurrent.com/scim/v2/Groups/1"}}]}
```

The response contains [these fields](../groups.html#list-response-fields).

### Pagination

The SCIM Groups API supports filtering as defined in [RFC 7644 - Pagination](https://tools.ietf.org/html/rfc7644#section-3.4.2.4)

startIndex
: **[integer]**, default: `1` — The 1-based index of the first query result.

count
: **[integer]**, default: `25` — Non-negative integer between 1 and 25 indicating the desired maximum number of results per page, e.g., 10.

Examples:

```
GET /scim/v2/Groups?startIndex=10&count=10
```

### Filtering

The SCIM Groups API partially supports filtering as defined in [RFC 7644 - Filtering](https://tools.ietf.org/html/rfc7644#section-3.4.2.2)

Filtering is available for the following attributes:
: - `displayName`
 - `externalId`
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
GET /scim/v2/Groups?filter=displayName eq "Skimming Corp"
GET /scim/v2/Groups?filter=displayName ne "Skimming Corp"
GET /scim/v2/Groups?filter=externalId eq "SCIM1"
GET /scim/v2/Groups?filter=meta.lastModified lt "2018-04-19T13:47:13Z"
GET /scim/v2/Groups?filter=meta.created gt "2018-04-19T13:47:13Z"
GET /scim/v2/Groups?filter=meta.lastModified gt "2018-04-19T13:47:13Z" and displayName eq "Skimming Corp"
GET /scim/v2/Groups?filter=displayName eq "Skimming Corp" or displayName eq "Skim Holland"
```

## Get a single group

```
GET /scim/v2/Groups/:id
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:schemas:core:2.0:Group"],"id":"1","externalId":"G1","displayName":"Widget Data Center","groupType":"Organization","members":[{"display":"card.skimmer@scim.com","value":"1","$ref":"https://<account>.xurrent.com/scim/v2/Users/1"},{"display":"jane.doe@scim.com","value":"2","$ref":"https://<account>.xurrent.com/scim/v2/Users/2"}],"meta":{"resourceType":"Group","created":"2018-04-17T11:05:29-05:00","lastModified":"2018-04-17T11:05:29-05:00","location":"https://<account>.xurrent.com/scim/v2/Groups/1"}}
```

The response contains [these fields](../groups.html#fields).

## Create a group

```
POST /scim/v2/Groups
```

When creating a new group [these fields](../groups.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"schemas":["urn:ietf:params:scim:schemas:core:2.0:Group"],"id":"5","...":"..."}
```

The response contains [all fields](../groups.html#fields) of the created group and is similar to the response in [Get a single group](../groups.html#get-a-single-group)

## Update a group

When using `PUT` the `members` will be replaced by the members provided in update call, if present.

```
PUT /scim/v2/Groups/:id
```

When using `PATCH` the members provided in update call, if present, will be added to the list of members of the group. If the `delete` operation is provided in the member hash, the member is removed from the list of members of the group. It behaves as described [in this draft spec](http://www.simplecloud.info/specs/draft-scim-api-00.html#edit-resource-with-patch).

```
PATCH /scim/v2/Groups/:id
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:schemas:core:2.0:Group"],"id":"5","...":"..."}
```

The response contains [all fields](../groups.html#fields) of the created group and is similar to the response in [Get a single group](../groups.html#get-a-single-group)

## Delete a group

When a group is deleted, all members will be automatically removed from that group.

```
DELETE /scim/v2/Groups/:id
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
: *Readonly* **[array]** — A multi-valued list of complex objects containing the requested resources containing [these fields](../groups.html#fields).

## Fields

As defined in the [Group Schema](../schemas.html#get-the-group-schema)

displayName
: **[string]** — A human-readable name for the Group that is unique to the service provider.

groupType
: **[hash]** — **specific for xurrent** The type of group. Typical values used might be ‘Organization’ or ‘Site’ but any string value may be used.

members
: **[array]** — A list of members of the Group.

 members.value
 : **[string]** — Identifier of the member of this Group.

 members.$ref
 : **[uri]** — The URI corresponding to a SCIM resource that is a member of this Group.

 members.operation
 : **[string]**, default: `add` — Only available on `PATCH` [update](../groups.html#update-a-group). Valid values are:
 : - `add` : Add the member to the group members
 - `delete`: Delete the member from the group members

 members.type
 : **[string]** — **specific for xurrent** A label indicating the type of resource, e.g., ‘User’ or ‘Group’.

meta.location
: **[string]** — The URI of this resource type.

meta.resourceType
: **[string]** — The name of the resource type.
