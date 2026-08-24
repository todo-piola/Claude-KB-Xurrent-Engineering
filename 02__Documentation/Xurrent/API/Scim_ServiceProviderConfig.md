# SCIM Service Provider Config API

- [Get the service provider config](index.html#get-the-service-provider-config)
- [Fields](index.html#fields)

## Get the service provider config

```
GET /scim/v2/ServiceProviderConfig
```

### Response

```
status: 200 OK
```

```
{"schemas":["urn:ietf:params:scim:schemas:core:2.0:ServiceProviderConfig"],"documentationUri":"https://developer.xurrent.com/v1/scim/","patch":{"supported":true},"bulk":{"supported":false,"maxOperations":0,"maxPayloadSize":0},"filter":{"supported":true,"maxResults":25},"changePassword":{"supported":false},"sort":{"supported":false},"etag":{"supported":false},"authenticationSchemes":[{"name":"OAuth Bearer Token","description":"Authentication scheme using the OAuth Bearer Token Standard","specUri":"http://www.rfc-editor.org/info/rfc6750","documentationUri":"https://developer.xurrent.com/v1/oauth/","type":"oauthbearertoken","primary":true},{"name":"HTTP Basic","description":"Authentication scheme using the HTTP Basic Standard","specUri":"http://www.rfc-editor.org/info/rfc2617","documentationUri":"https://developer.xurrent.com/v1/#authentication","type":"httpbasic"}],"meta":{"location":"https://<account>.xurrent.com/scim/v2/ServiceProviderConfig","resourceType":"ServiceProviderConfig","created":"2018-03-23T00:00Z","lastModified":"2018-03-23T00:00Z","version":"1"}}
```

The response contains [these fields](index.html#fields).

## Fields

Definitions taken from [RFC 7643 - Service Provider Configuration Schema](https://tools.ietf.org/html/rfc7643#section-5)

documentationUri
: *Readonly* **[string]** — An HTTP-addressable URL pointing to the service provider’s human-consumable help documentation.

patch.supported
: *Readonly* **[boolean]** — Specifying whether or not the PATCH operation is supported.

bulk.supported
: *Readonly* **[boolean]** — Specifying whether or not the bulk operation is supported.

bulk.maxOperations
: *Readonly* **[integer]** — The maximum number of operations for a bulk operation.

bulk.maxPayloadSize
: *Readonly* **[integer]** — The maximum payload size in bytes for a bulk operation.

filter.supported
: *Readonly* **[boolean]** — Specifying whether or not filtering is supported.

filter.maxResults
: *Readonly* **[boolean]** — The maximum number of resources returned in a filtered response.

changePassword.supported
: *Readonly* **[boolean]** — Specifying whether or not changing a password is supported.

sort.supported
: *Readonly* **[boolean]** — Specifying whether or not custom sorting is supported.

etag.supported
: *Readonly* **[boolean]** — Specifying whether or not e-tags are supported.

authenticationSchemes
: *Readonly* **[array]** — List of the supported authentication scheme properties.

authenticationSchemes.type
: *Readonly* **[string]** — The authentication scheme.

authenticationSchemes.name
: *Readonly* **[string]** — Human readable name of the authentication scheme, one of `oauth`, `oauth2`, `oauthbearertoken`, `httpbasic`, or `httpdigest`.

authenticationSchemes.description
: *Readonly* **[string]** — Human readable description of the authentication scheme.

authenticationSchemes.specUri
: *Readonly* **[uri]** — An HTTP-addressable URL pointing to the authentication scheme’s specification.

authenticationSchemes.documentationUri
: *Readonly* **[uri]** — An HTTP-addressable URL pointing to the authentication scheme’s usage documentation.

meta.location
: *Readonly* **[string]** — The URI of this service provider config.

meta.resourceType
: *Readonly* **[string]** — The name of the resource type of this service provider config.

meta.created
: *Readonly* **[datetime]** — The moment that the resource was added to the service provider.

meta.lastModified
: *Readonly* **[datetime]** — The most recent moment that the details of this resource were updated at the service provider.

meta.version
: *Readonly* **[string]** — The version of the resource being returned.
