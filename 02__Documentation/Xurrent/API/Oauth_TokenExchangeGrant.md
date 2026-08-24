# OAuth - Token Exchange Grant

The [RFC 8693](https://tools.ietf.org/html/rfc8693) Token Exchange grant allows
external systems holding third-party identity tokens (e.g. a Teams bot with an
Azure AD JWT) to exchange a verified external JWT for a short-lived Xurrent
bearer token tied to a resolved person. This enables machine-to-machine flows
where the calling system already has a trusted identity token from an OpenID
Connect identity provider.

- [Overview](index.html#overview)
- [Prerequisites](index.html#prerequisites)
- [Access Token Request](index.html#access-token-request)

## Overview

The token exchange flow works as follows:

1. The external system obtains a JWT from its identity provider (e.g. Azure AD,
 Okta, Google) through the provider’s normal authentication flow.
2. The external system sends an [access token request](index.html#access-token-request) to
 Xurrent’s `/token` endpoint, providing:

 - the client ID of the OAuth application registered in Xurrent,
 - the client secret of the OAuth application registered in Xurrent,
 - the external JWT (the “subject token”), and
 - the subject token type.
3. Xurrent validates the subject token:

 - the token’s signature is verified using the identity provider’s published
 JSON Web Key Set (JWKS), discovered via
 [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html),
 - the issuer is validated against the linked SSO configuration,
 - the audience matches the application’s configured audience value, and
 - the token has not expired.
4. Xurrent resolves the person from the validated token claims using the SSO
 configuration’s identifier setting (primary email or authentication ID),
 searching the application’s account and its directory account.
5. Xurrent issues a short-lived access token (valid for 1 hour) tied to the
 resolved person and the application’s configured scopes. No refresh token is
 issued — callers must re-exchange when the token expires.
6. The external system uses the access token to make Xurrent API requests. The
 token carries the application’s scopes and the resolved person’s identity.

## Prerequisites

Before using the token exchange grant, the following must be configured:

- An **OIDC SSO configuration** in the Xurrent account (or its directory
 account) that corresponds to the external identity provider. This SSO
 configuration provides issuer trust, JWKS discovery, and the person resolution
 strategy.
- An **OAuth application** registered in Xurrent with:

 - **Grant type** set to *Token Exchange*
 - **SSO Configuration** linked to the OIDC SSO configuration above
 - **Audience** set to the expected `aud` claim value in the external JWT
 - **Scopes** configured to the permissions the application requires

## Access Token request

```
POST https://oauth.xurrent.com/token
```

### Parameters

*Please note:* These parameters must be passed via the body of the POST request.

client\_id
: *Required* **[string](../../general/data_types.html)** - The client ID that belongs
 to the OAuth application registered in Xurrent.

client\_secret
: *Required* **[string](../../general/data_types.html)** - The client secret you
 received from Xurrent when you registered the OAuth application in Xurrent.

grant\_type
: *Required* **[string](../../general/data_types.html)** - Must be set to
 `urn:ietf:params:oauth:grant-type:token-exchange`.

subject\_token
: *Required* **[string](../../general/data_types.html)** - The external JWT obtained
 from the identity provider. This token will be validated against the identity
 provider’s published JWKS.

subject\_token\_type
: *Required* **[string](../../general/data_types.html)** - Must be set to
 `urn:ietf:params:oauth:token-type:jwt`.

### Response

For valid requests, the client will receive a response with HTTP status code 200, containing:

access\_token
: *Required* **[string](../../general/data_types.html)** - Temporary OAuth access
 token. Allows the external system to make Xurrent API requests as the resolved
 person, constrained by the application’s configured scopes.
 The token expires after 1 hour. No refresh token is issued — the caller must
 perform a new token exchange to obtain a fresh access token.
 The token becomes invalid when:

 - the token belonging to the `client_id` and `client_secret` is disabled or
 deleted,
 - the application is disabled,
 - the resolved person is disabled.

issued\_token\_type
: *Required* **[string](../../general/data_types.html)** -
 `urn:ietf:params:oauth:token-type:access_token`.

token\_type
: *Required* **[string](../../general/data_types.html)** - `bearer`.

expires\_in
: *Required* **[integer](../../general/data_types.html)** - The number of seconds
 until the access token expires (3600).

### Error Responses

For invalid requests an error response with HTTP status code 400 will be returned, containing:

error
: *Required* **[string](../../general/data_types.html)** - [Code](https://datatracker.ietf.org/doc/html/rfc6749#section-5.2) indicating why the request was invalid. Possible values:

 - `invalid_request` — a required parameter is missing or has an invalid value (e.g. wrong `subject_token_type`)
 - `invalid_grant` — the subject token failed validation (expired, wrong issuer, wrong audience, invalid signature, OIDC discovery failure) or the person could not be resolved
 - `unsupported_grant_type` — the `grant_type` value is not recognized

error\_description
: *Optional* **[string](../../general/data_types.html)** - Additional information on why the request was invalid.
