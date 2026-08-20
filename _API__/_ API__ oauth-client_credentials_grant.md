# OAuth - Client Credentials Grant

The image above illustrates the following 5 steps that complete an OAuth Client
Credentials Grant flow from 3rd party applications:

1. The third-party application performs an [access token request](../client_credentials_grant.html#access-token-request)
 to request an access token. The following data is provided by the
 application:

 - the client ID of the application record in Xurrent, and
 - the client secret of the application record in Xurrent
2. Xurrent then generates a temporary access token.

 The access token allows the third-party application to retrieve data from Xurrent
 using the user linked to the application. An access token is valid only for 1
 hour.

 Xurrent returns the access token to the third-party application.
3. The third-party application uses the access token to make Xurrent API requests.
4. Xurrent returns API responses to the third-party application.
5. The third-party application uses the data received in the API responses to
 render a page for the user or perform a background action.

## Access Token request

```
POST https://oauth.xurrent.com/token
```

### Parameters

client\_id
: *Required* **[string](../../general/data_types.html)** - The client ID that belongs
 to the application record registered in Xurrent.

client\_secret
: *Required* **[string](../../general/data_types.html)** - The client secret you
 received from Xurrent when you registered the application in Xurrent.

grant\_type
: *Required* **[string](../../general/data_types.html)** - Must be set to
 `client_credentials`.

### Response

Valid requests will receive a response with HTTP status code 200, containing:

access\_token
: *Required* **[string](../../general/data_types.html)** - Temporary OAuth access
 token. Allows the 3rd party application to retrieve data from Xurrent on behalf of
 the user.
 The token expires after 1 hour. The token becomes invalid when:

 - the token belonging to the `client_id` and `client_secret` is disabled or
 deleted,
 - the application is disabled.

For invalid requests a error response with HTTP status code 400 will be returned, containing:

error
: *Required* **[string](../../general/data_types.html)** - [Code](https://datatracker.ietf.org/doc/html/rfc6749#section-5.2) indicating why the request was invalid.

error\_description
: *Optional* **[string](../../general/data_types.html)** - Additional information on why the request was invalid.
