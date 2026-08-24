# OAuth - Authorization Code Grant

The OAuth Authorization Code Grant allows third-party applications to access
data on behalf of users in Xurrent after authorization of the application by these
users.

- [Overview](../authorization_code_grant.html#overview)
- [Authorization Request](../authorization_code_grant.html#authorization-request)
- [Access Token Request](../authorization_code_grant.html#access-token-request)
- [Refresh Token Requst](../authorization_code_grant.html#refresh-token-request)

## Overview

The image above illustrates the following 10 steps that complete an OAuth
Authorization Code Grant flow from third-party applications:

1. A user clicks on a login or authorization link within the third-party
 application. The third-party application now needs to retrieve data that the
 user is allowed to access in Xurrent.
2. The third-party application redirects the user to perform an
 [authorization request](../authorization_code_grant.html#authorization-request) to retrieve an authorization
 code. The redirect contains the following information that is required to
 perform the authorization request:

 - the client ID of the application record in Xurrent
 - the redirect URI - this is the web address to which the user is sent after
 access is granted.
3. The user follows the redirect to perform the authorization request.
4. Xurrent checks if the user has previously authorized the third-party application
 to access Xurrent.

 If authorization was already provided, the flow continues with step **8**.

 If not, Xurrent will redirect the user to an authorization prompt.
5. The user follows the redirect to the authorization prompt.
6. Xurrent displays the authorization prompt. The authorization propmpt asks the
 user to either ‘Deny’ or ‘Allow’ the third-party application access to Xurrent.
7. The user either allows or denies access to the third-party application.

 If the user denies, the flow ends by redirecting the user back to the
 third-party application with an error message that the third-party
 application can process.

 If the user allows access, this authorization is registered in Xurrent.
8. Xurrent generates an authorization code and redirects the user to the third-party
 application using the [authorization response](../authorization_code_grant.html#authorization-response)
 containing the code.
9. The user follows the redirect to the third-party application.
10. The third-party application performs an [access token request](../authorization_code_grant.html#access-token-request)
 to request an access token and a refresh token. The following data is
 provided by the application:

 - the client ID of the application record in Xurrent,
 - the client secret of the application record in Xurrent,
 - the authorization code the application received from Xurrent in step **7**, and
 - the redirect URI that was provided in step **2**.
11. Xurrent generates a temporary access token and a refresh token. The access token
 allows the third-party application to retrieve data from Xurrent on behalf of
 the user. An access token is valid only for 1 hour. The refresh token allows
 the third-party application to retrieve a new access token and refresh token
 when the access token expires (see [refresh token request](../authorization_code_grant.html#refresh-token-request).
 A refresh token is valid for 2 weeks.
 Xurrent returns these two tokens to the third-party application.
12. The third-party application uses the tokens to make Xurrent API requests.
13. Xurrent returns API responses to the third-party application.
14. The third-party application uses the data received in the API responses
 to render a page for the user or perform a background action.

---

It is important to point out that after a user has permitted a third-party
application access to Xurrent in step **7**, the user is able to see this in the
‘Access & Security’ section when the user opens ‘My Profile’ in Xurrent.

This is also where users can revoke the permissions they provided to third-party
applications.
When a user revokes the authorization from an application,
the access tokens that the application obtained from Xurrent for the user
immediately stop working.

## Authorization request

```
GET https://oauth.xurrent.com/authorize
```

### Parameters

client\_id
: *Required* **[string](../../general/data_types.html)** - The client ID that belongs
 to the application registered in Xurrent.

response\_type
: *Required* **[string](../../general/data_types.html)** - Must be set to `code`.

redirect\_uri
: *Required* **[string](../../general/data_types.html)** - URL in the application
 where users will be sent after authorization. The redirect URL must match one of
 the endpoints of the application registered in Xurrent.

state
: *Optional* **[string](../../general/data_types.html)** - Optional state value that
 can be used by the client to prevent cross-site request forgery. The state is
 included in the redirect to the `redirect_uri` after authorization by the user.
 The client should verify that the state as provided in this authorization
 request is the same as the state in the authorization callback.

### Response

For successful authorization requests, the client will receive a redirect to the
third-party application authorization page.

```
status: 302 Found
Location: https://example.xurrent.com/oauth/authorize_application?token
```

For invalid authorization requests, the client will receive a redirect to the
third-party application endpoint as provided in the authorization request (in
the following example [https://my-app.com/oauth/callback](https://my-application.com/oauth/callback)
is used).

```
status: 302 Found
Location: https://my-app.com/oauth/callback
```

The endpoint will receive the following parameters:

error
: *Required* **[string](../../general/data_types.html)** - Error code with one of the
 following values:

 - `invalid_request`
 - `access_denied` - when the user denied the authorization request
 - `server_error`
 - `temporarily_unavailable`

error\_description
: *Required* **[string](../../general/data_types.html)** - Human-readable text
 providining addition information about the error.

state
: *Optional* **[string](../../general/data_types.html)** - Required when “state”
 parameter was present in the authorization request. Contains the exact value as
 received from the client.

## Authorization Response

After following the redirect from a successful authorization request, the
authorization page is displayed where the user can either allow or deny access
to the third-party application.

When the user authorizes the third-party application, a redirect response to the
third-party application endpoint as provided in the authorization request will
occur.

```
status: 302 Found
Location: https://my-app.com/oauth/callback
```

The endpoint will receive the following parameters:

code
: *Required* **[string](../../general/data_types.html)** - Authorization code
 generated by the Xurrent application. This code expires after 10 minutes and can
 only be used once. If it is used more than once, all previous access tokens that
 were generated using that authorization code will become invalid.

state
: *Optional* **[string](../../general/data_types.html)** - Required when “state”
 parameter was present in the authorization request. Contains the exact value as
 received from the client.

When the user denies access to the third-party application, a redirect response
to the third-party application endpoint as provided in the authorization request
will occur.

```
status: 302 Found
Location: https://my-app.com/oauth/callback
```

The endpoint will receive the same parameters as described in the error response
in [Response](../authorization_code_grant.html#response).

## Access Token request

```
POST https://oauth.xurrent.com/token
```

### Parameters

*Please note:* These parameters must be passed via the body of the POST request.

client\_id
: *Required* **[string](../../general/data_types.html)** - The client ID that belongs
 to the application record registered in Xurrent.

client\_secret
: *Required* **[string](../../general/data_types.html)** - The client secret you
 received from Xurrent when you registered the application in Xurrent.

redirect\_uri
: *Required* **[string](../../general/data_types.html)** - Must match the redirect URL
 that was used in the [Authorization request](../authorization_code_grant.html#authorization-request).

code
: *Required* **[string](../../general/data_types.html)** - The authorization code you
 received in the redirect after the user authorizes the third-party application.

grant\_type
: *Required* **[string](../../general/data_types.html)** - Must be set to
 `authorization_code`.

### Response

For successful access token requests, the client will receive a response
containing the following parameters:

access\_token
: *Required* **[string](../../general/data_types.html)** - Temporary OAuth access
 token. Allows the third-party application to retrieve data from Xurrent on behalf of
 the user.
 The token becomes expires after 1 hour. The refresh token can be used to
 generate a new access token. The token becomes invalid when:

 - when the user revokes the authorization. The user will have to re-authorize
 the application.
 - when the scopes of the application is changed. The user will have to
 re-authorize the application.
 - the token belonging to the `client_id` and `client_secret` is disabled or
 deleted,
 - when the application is disabled.

refresh\_token
: *Required* **[string](../../general/data_types.html)** - OAuth refresh token. Allows
 the third-party application to retrieve a new access token (and refresh token)
 when the access token expires.
 The refresh token becomes expires after 2 weeks. The token becomes invalid for
 the same reasons as listed with the `access_token`.

For invalid access token requests a error response as described in
[Response](../authorization_code_grant.html#response) will be returned.

## Refresh Token request

```
POST https://oauth.xurrent.com/token
```

### Parameters

*Please note:* These parameters must be passed via the body of the POST request.

client\_id
: *Required* **[string](../../general/data_types.html)** - The client ID that belongs
 to the application record registered in Xurrent.

client\_secret
: *Required* **[string](../../general/data_types.html)** - The client secret you
 received from Xurrent when you registered the application record in Xurrent.

refresh\_token
: *Required* **[string](../../general/data_types.html)** - The refresh token you
 received from the Access Token request or a previous Refresh Token request.

grant\_type
: *Required* **[string](../../general/data_types.html)** - Must be set to
 `refresh_token`.

### Response

For successful refresh token requests, the client will receive a response
containing the following parameters:

access\_token
: *Required* **[string](../../general/data_types.html)** - Temporary OAuth access
 token. Allows the third-party application to retrieve data from Xurrent on behalf of
 the user.
 The token expires after 1 hour. The refresh token can be used to
 generate a new access token. The token becomes invalid when:

 - when the user revokes the authorization. The user will have to re-authorize
 the application.
 - when the scopes of the application is changed. The user will have to
 re-authorize the application.
 - the token belonging to the `client_id` and `client_secret` is disabled or
 deleted,
 - when the application is disabled.

refresh\_token
: *Required* **[string](../../general/data_types.html)** - OAuth refresh token. Allows
 the third-party application to retrieve a new access token (and refresh token)
 when the access token expires.
 The refresh token becomes expires after 2 weeks. The token becomes invalid for
 the same reasons as listed with the `access_token`.

For invalid refresh token requests a error response as described in
[Response](../authorization_code_grant.html#response) will be returned.
