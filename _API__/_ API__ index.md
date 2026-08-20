# Xurrent REST API - Introduction

This page offers an introduction to the REST (or [Representational State Transfer](http://en.wikipedia.org/wiki/Representational_state_transfer)) API of the Xurrent service. This API is used for retrieving, creating and updating Xurrent records like Requests, Workflows, CIs, Services, SLAs, People, etc.

The following topics are covered in this introduction:

- [Service URL](index.html#service-url)
- [Schema](index.html#schema)
- [HTTP Verbs](index.html#http-verbs)
- [Mime Type](index.html#mime-type)
- [Authentication](index.html#authentication)
- [Multiple Accounts](index.html#multiple-accounts)
- [Internationalization](index.html#internationalization)
- [Rate Limiting](index.html#rate-limiting)
- [Error Codes & Responses](index.html#http-status-codes)

Information about generic REST API functionality like [Pagination](general/pagination.html) or [Filtering](general/filtering.html), can be found in the submenu below the *General* option on the right. The [Libraries](general/libraries.html) page offers links to client libraries to simplify usage of the REST API.

## Service URL

The Xurrent API requires a point of entry service URL that references the instance
of a specific environment and region:

| Instance | Environment | Region |
| --- | --- | --- |
| `https://api.xurrent.com/v1` | Production | Global |
| `https://api.au.xurrent.com/v1` | Production | Australia |
| `https://api.uk.xurrent.com/v1` | Production | United Kingdom |
| `https://api.ch.xurrent.com/v1` | Production | Switzerland |
| `https://api.us.xurrent.com/v1` | Production | United States |
| `https://api.xurrent.qa/v1` | Quality Assurance | Global |
| `https://api.au.xurrent.qa/v1` | Quality Assurance | Australia |
| `https://api.uk.xurrent.qa/v1` | Quality Assurance | United Kingdom |
| `https://api.ch.xurrent.qa/v1` | Quality Assurance | Switzerland |
| `https://api.us.xurrent.qa/v1` | Quality Assurance | United States |
| `https://api.xurrent-demo.com/v1` | Demo | Global |

Please note the use of https:// in the URL above. All Xurrent API communication is encrypted over HTTPS. Any non-secure requests are automatically rejected, so we recommend establishing a test connection with the secure API entry point before sending sensitive data.

```
$ curl -i https://api.xurrent.com/v1
```

```
status: 200 OK
content-type: application/json; charset=utf-8
content-length: 2
```

```
{}
```

## Schema

All data is sent and received as JSON.

```
$ curl -i https://api.xurrent.com/v1/me
```

```
status: 200 OK
content-type: application/json; charset=utf-8
x-ratelimit-limit: 3600
x-ratelimit-remaining: 3542
content-length: 2198
```

```
{"name":"My User Name","site":{"name":"My Site Name","id":13},"...":"..."}
```

See the [Data Types section](general/data_types.html) for detailed information on the formatting of the values.

## HTTP Verbs

The API is RESTful, meaning that the HTTP verbs are used for specific actions.

GET
: Used for retrieving resources.

POST
: Used for creating resources, or to link resources.

PATCH
: Used for updating resources with partial JSON data. PATCH is a relatively new and uncommon HTTP verb, so resource endpoints also accept PUT requests.

DELETE
: Used to remove a resource from a collection.

## Mime Type

The only mime type the Xurrent API supports is:

```
application/json
```

Xurrent does not define any custom mime types.

You may explicitly set the `Accept` header when you make a request
and/or end the path with `.json`. If both are omitted Xurrent defaults
to returning a JSON response.

The following are all equivalent:

```
$ curl -H "Accept: application/json" https://api.xurrent.com/v1/me

$ curl https://api.xurrent.com/v1/me.json

$ curl https://api.xurrent.com/v1/me
```

## Authentication

When you are using the Xurrent REST API, it is always through an existing user in Xurrent.
There is no special API user.
When authenticating as an existing user in Xurrent, you can access the data that the user
can access, and perform the actions that the user is authorized to perform.

Each request to the Xurrent REST API must supply two HTTP headers:

- `Authorization: Bearer <oauth-token>`
- `X-Xurrent-Account: <accountID>`

You can obtain an OAuth token either by generating a Personal Access Token from My Profile in Xurrent,
or by creating an OAuth Application from the Settings console in Xurrent.

The Xurrent account ID value passed in the `X-Xurrent-Account` header determines the current account that the API request will use.

### Personal Access Tokens

A personal access token is an OAuth Token, and must be provided as part of the Bearer Authentication:

```
$ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 https://api.xurrent.com/v1/me
```

Note that for this example to work your personal access token must have added a scope to allow action `me - All`.

Your personal access tokens can be found by clicking on your avatar in the upper right corner, and selecting the menu option *My Profile*

Open the *Personal Access Tokens* section, click on the *Generate token* button to generate a new token.

After saving the form, the new token is displayed:

To simplify onboarding for integrations, you can create [Templated Token URLs](oauth/templated_tokens/index.html) that pre-fill the token creation form with a specific name and scopes.

## Multiple Accounts

Often the account of the authenticated user has several trust relations with other accounts.
As a result, resources from other accounts (mostly SLA’s, Requests, Teams and People) are accessible through the API.

Each reference to a resource that belongs to a different account will receive an `account` hash with the `name` and `id` of
that account, see [references](general/data_types.html#account) for more details.

### Switching Accounts

The authenticated user may have access rights to one or more trusted accounts.
To retrieve information from those accounts through the API, add the `X-Xurrent-Account` header to the API request.

In this example the authenticated user has access to the Widget North America account:

```
 $ curl -H "X-Xurrent-Account: wna-it" https://api.xurrent.com/v1/sites?fields=name
```

```
status: 200 OK
```

```
[{"name":"Widget Data Center","id":14},{"name":"Widget International Headquarters","id":15},{"name":"Widget Manufacturing Center","id":16},{"name":"Widget Research & Development Center","id":17}]
```

And the Widget Europe account:

```
 $ curl -H "X-Xurrent-Account: weu-it" https://api.xurrent.com/v1/sites?fields=name
```

```
status: 200 OK
```

```
[{"name":"Widget European Headquarters","id":18}]
```

## Internationalization

Most API calls are language independent. In some cases the response contains translated values, e.g.:

- within the [enumerations](general/enumerations/index.html)
- within [validation errors](index.html#unprocessable-entity---semantic-error-in-provided-data)

By default the language of the authenticated user is taken, see the *Personal Preferences* screen found
under the *Settings* menu in Xurrent. To override this setting, add the `X-Xurrent-Language` header
to the API request.

```
 $ curl -H "X-Xurrent-Language: nl" https://api.xurrent.com/v1/enums
```

```
status: 200 OK
```

```
{"request.status":[{"id":"declined","txt":"Geweigerd"},{"id":"assigned","txt":"Toegewezen"},{"id":"accepted","txt":"Geaccepteerd"},{"id":"etc","txt":"etc"}],"etc":"..."}
```

All supported language codes can be found via the [Enumerations](general/enumerations/index.html) API, see the `language` key:

```
{"language":[{"id":"en-US","txt":"English (United States)"},{"id":"nl","txt":"Nederlands"},{"id":"fr","txt":"Francais"},{"id":"da","txt":"Dansk"},{"id":"et","txt":"Eesti"},"..."]}
```

## Rate Limiting

Authenticated API requests are associated with the authenticated user.
Unauthenticated API requests are associated with the originating IP address, and not the user making requests.

The returned HTTP headers of an API request show the current rate limit status:

```
$ curl -i https://api.xurrent.com/v1/me
```

```
status: 200 OK
x-ratelimit-limit: 3600
x-ratelimit-remaining: 3599
x-ratelimit-reset: 1533873527
```

x-ratelimit-limit
: The maximum number of requests permitted to make in the current rate limit window.

x-ratelimit-remaining
: The number of requests remaining in the current rate limit window.

x-ratelimit-reset
: The time at which the current rate limit window resets in [UTC epoch seconds](http://en.wikipedia.org/wiki/Unix_time).

If the reset time is needed in a different format then any modern programming
language can be used to achieve this. For example, if opening up the console
of a web browser, the reset time can be returned as a JavaScript Date object
as follows:

```
new Date(1533873527 * 1000)
=> Fri Aug 10 2018 03:58:47 GMT+0000 (UTC)
```

You can [check your rate limit status](rate_limit.html) without incurring an API hit,
but accessing this endpoint is limited to once per second.

### Responding to Rate Limiting Conditions

Once a rate limit window is exceeded an error response is returned and the
HTTP header `retry-after` indicates how long to wait (in seconds) before
making a new request:

```
status: 429 Too Many Requests
content-type: application/json; charset=utf-8
retry-after: 30
```

```
{"message":"Too Many Requests","documentation_url":"https://developer.xurrent.com/v1/#rate-limiting"}
```

This response instructs your app to wait 30 seconds before attempting to send a new request.

By programmatically evaluating the `retry-after` header you can wait for the indicated number
of seconds before retrying the same request.

## HTTP Status Codes

The Xurrent API attempts to return appropriate [HTTP status codes](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes) for every request.

### `200 OK` - Success!

```
 $ curl https://api.xurrent.com/v1/me
```

```
status: 200 OK
content-type: application/json; charset=utf-8
```

### `204 No Content` - Success, no data to return

```
 $ curl https://api.xurrent.com/v1/me
```

```
status: 200 OK
content-type: application/json; charset=utf-8
```

### `304 Not Modified` - There was no new data to return

```
 $ curl -H 'Etag: 1234567890' https://api.xurrent.com/v1/me
```

```
status: 304 Not Modified
content-type: application/json; charset=utf-8
```

### `400 Bad Request` - Incorrect parameter values or syntax error in JSON

```
 $ curl -i https://api.xurrent.com/v1/cis?per_page=-10
```

```
status: 400 Bad Request
content-type: application/json; charset=utf-8
```

```
{"message":"Parameter 'per_page' cannot be less than 1"}
```

### `401 Unauthorized` - Invalid or missing authentication credentials

```
 $ curl -i -u "user:invalid" https://api.xurrent.com/v1/me
```

```
status: 401 Unauthorized
content-type: application/json; charset=utf-8
```

```
{"message":"Unauthorized"}
```

### `403 Forbidden` - Access to resource is not allowed with current credentials

```
 $ curl -i https://api.xurrent.com/v1/people/1
```

```
status: 403 Forbidden
content-type: application/json; charset=utf-8
```

```
{"message":"Forbidden"}
```

### `404 Not Found` - The URI is invalid or the resource requested does not exist

```
 $ curl -i https://api.xurrent.com/v1/me_too
```

```
status: 404 Not Found
content-type: application/json; charset=utf-8
```

```
{"message":"Not Found"}
```

### `406 Not Acceptable` - URI is known but does not accept JSON API requests

```
 $ curl -i https://api.xurrent.com/v1/account/billing
```

```
status: 406 Not Acceptable
content-type: application/json; charset=utf-8
```

```
{"message":"Not Acceptable"}
```

### `422 Unprocessable Entity` - Semantic error in provided data

```
 $ curl -i -X POST -F impact=medium https://api.xurrent.com/v1/requests
```

```
status: 422 Unprocessable Entity
content-type: application/json; charset=utf-8
```

```
{"message":"Validation Failed","errors":[["subject","Subject can't be blank"],["category","Category can't be blank"]]}
```

The validation errors are tuples with the field name and a [localized](index.html#internationalization) error message.
Note that a single field may yield multiple validation errors.

### `429 Too Many Requests` - Rate Limit Exceeded

```
status: 429 Too Many Requests
content-type: application/json; charset=utf-8
x-ratelimit-limit: 3600
x-ratelimit-remaining: 0
x-ratelimit-reset: 1533873527
retry-after: 30
```

```
{"message":"Too Many Requests","documentation_url":"https://developer.xurrent.com/v1/#rate-limiting"}
```

### `500 Internal Server Error` - Something is broken. The Xurrent team should investigate.

```
status: 500 Internal Server Error
content-type: application/json; charset=utf-8
```

```
{"message":"Internal Server Error"}
```

### `502 Bad Gateway` - Xurrent is down or being upgraded

```
status: 502 Bad Gateway
content-type: application/json; charset=utf-8
```

```
{"message":"Bad Gateway"}
```

### `503 Service Unavailable` - The Xurrent servers are up, but overloaded with requests. Try again later.

```
status: 503 Service Unavailable
content-type: application/json; charset=utf-8
```

```
{"message":"Service Unavailable"}
```

### `504 Gateway timeout` - The Xurrent servers are up, but the request could not be serviced due to some failure at Xurrent. Try again later.

```
status: 504 Gateway timeout
content-type: application/json; charset=utf-8
```

```
{"message":"Gateway timeout"}
```

If you see an error response which is not listed in the above table, then fall back to the HTTP status code in order to determine the best way to address the error.
