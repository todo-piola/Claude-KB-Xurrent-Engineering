# Data Types

All data is sent and received as JSON.

- [Output](../data_types.html#output): The formatting of values in the responses.
- [Input](../data_types.html#input): The formatting of input parameters of requests.
- [References](../data_types.html#references): Composition of references in the responses.
- [Attachments](../data_types.html#attachments): Composition of attachments in the requests.

## Output

**boolean**
: *native*

 `"known_error": true`

**currency**
: *string*: one of the currencies defined in the [enumeration](https://api.xurrent.com/v1/enums.html#account.currency)

`"currency": "usd"`

**custom fields**
: *array of hashes*: each hash has keys `id` and `value`

```
 "custom_fields": [
 {"id": "first_name", "value": "Howard"},
 {"id": "last_name", "value": "Tanner"}
 ]
```

**date**
: *string: yyyy-mm-dd*

 `"start_date": "2011-06-24"`

**datetime**
: *string: yyyy-mm-ddThh:mm*

 `"start_at": "2010-12-30T23:00"`

 ISO 8601 format, with a minutes resolution, without timezone.

**decimal**
: *string*: number with decimals, separated by a dot (.)

 `"cost_per_hour": "120.5"`

**duration**
: *integer*: with resolution in minutes

 `"response_target": 240`

**enum**
: *string*: one of the options defined for the [enumeration](../enumerations/index.html)

 `"status": "registered"`

**float**
: *native*

 `"rate": 3.2313`

**integer**
: *native*

 `"nr_of_cores": 3`

**null**
: *native*: all blank fields are included as `null` instead of being omitted

 `"solved_at": null`

**reference**
: *hash*: [composed of multiple values](../data_types.html#references), or *null* if the reference is not filled out

 `"team": {"id": 12, "name": "Service Desk"}`
 `"team": null`

**string, text**
: *native*

 `"name": "Windows for Sales Tracking Production"`

**timestamp**
: *string: yyyy-mm-ddThh:mm:ssZ*

 `"completed_at": "2010-01-05T23:00:00Z"`

 ISO 8601 format, with a seconds resolution, with timezone.

**time of day**
: *string: hh:mm*

 `"time_from": "08:30"`

 In [military format](http://en.wikipedia.org/wiki/24-hour_clock). 00:00 = midnight at the start of the day, 12:00 = noon, 24:00 = midnight at the end of the day

**time zone**
: *string*: one of the time zones defined in the [enumeration](https://api.xurrent.com/v1/enums.html#time_zone)

 `"time_zone": "Central Time (US & Canada)"`

## Input

**attachments**
: An array of references to uploaded file [attachments](../data_types.html#attachments)

**boolean**
: Truthy values are `1`, `T`, `Y`, `TRUE`, `YES`, `ON`. These values are case insensitive, so `true`, `trUE`, `tRue` are all treated as truthy values.
 Falsy values are anything else, like: `false`, `f`, `FALSE`, `F`, `0`

 `?known_error=true`

**enum**
: One of the options defined for the [enumeration](../enumerations/index.html)

 `?status=registered`

**date**
: *yyyy-mm-dd*

 `?start_date=2011-06-24`

**datetime**
: *yyyy-mm-ddThh:mm*

 `?start_at=2010-12-30T23:00`

 ISO 8601 format (with a minutes resolution, without timezone)

**decimal, float**
: any number with decimals, separated by a dot (.)

 `?rate=3.2313`

**duration**
: *integer*: with resolution in minutes

 `?response_target=150`

 Alternatively it accepts a string in the format `hhh:mm`, for example:

 `?response_target=2:30`

**integer**
: any integer (0, 1, 2, …)

 `?nr_of_cores=3`

**null**
: all blank fields should be omitted from the input

**reference**
: the `id` of the referenced resource, always append `_id` to the field name

 `?team_id=12`

 For arrays of references always append `_ids` to the field name

```
 "ci_ids": [1763, 1764]
```

**string, text**
: any value

 `?name=Windows%20for%20Sales%20Tracking%20Production`

**timestamp**
: *yyyy-mm-ddThh:mm:ssZ*

 `?completed_at=2010-01-05T23:00:00Z`

 ISO 8601 format (with a seconds resolution, with timezone)

**time of day**
: *hh:mm*

 `?time_from=08:30`

 In [military format](http://en.wikipedia.org/wiki/24-hour_clock). 00:00 = midnight at the start of the day, 12:00 = noon, 24:00 = midnight at the end of the day

**time zone**
: any valid time zone identifier listed in one of the following sources:

 - [enumeration of time zones](https://api.xurrent.com/v1/enums.html#time_zone)
 - [Time Zone Database](https://www.iana.org/time-zones)

 Time zone values from the [Time Zone Database](https://www.iana.org/time-zones)
 are mapped onto the [enumeration of time zones in Xurrent](https://api.xurrent.com/v1/enums.html#time_zone)
 by their UTC offset.

 `?time_zone=Europe/Amsterdam`

## References

A reference to another resource is composed of one or more of the following fields.

*Note*: In the [input](../data_types.html#input), use only the `id` of the referenced resource and append `_id` to the field name, e.g. `?team_id=12`.
For fields that contain an array of references as input, use the singular field name and append `_ids`, e.g. `service_instance_ids` for ‘service\_instances’.

### ID

All references contain an `id` property with which the details of the resource can be retrieved using a separate API call.

Note that when a record is opened in the Xurrent user interface, the `id` can be found in the Address bar of the browser. It is the unique identifier at the end of the URL. The `id` of an account can be found in the user interface by going to the Account Overview section of the Settings console.

For aggregated references (arrays of ~) an `id` is not returned. Instead, all available fields are contained in aggregated references so that an `id` is not needed.

The `:id` URL path parameter accepts either the numeric `id` or the `nodeID` returned by the [GraphQL API](https://developer.xurrent.com/graphql/). For example, both `GET /v1/people/12` and `GET /v1/people/NG1lLmNvbS9QZXJzb24vMTI` return the same record. The same applies to nested resources, e.g. `GET /v1/cis/<nodeID>/users` and `POST /v1/cis/<nodeID>/users/<nodeID>`. Note that this only applies to the `:id` in the URL — references in the request body (e.g. `team_id`) currently still require the numeric id.

### Display Properties

The reference will always contain the properties necessary to display the (list of) reference(s) to the end-user.
In most cases this will expose the `name` and/or `subject` properties, but there are some exceptions like
`label` for Configuration Item references.

### Account

When the account of the referenced resource is different from the account of the authenticated user,
the `account` reference will be provided. The `account` field is itself a reference and will always only
show `name` and `id`. The `name` is intended as a display property for the end-user. The `id`
can be used to switch to that account if appropriate, see [Multiple Accounts](../../index.html#multiple-accounts).

If a resource or reference to a resource does not expose an `account` field, the account of the resource is equal to the account of the authenticated user.

The following example shows a request that is completed by a member of the Service Desk team from a different account (Virtual Support).

```
 $ curl -H "Authorization: Bearer <oauth-token>" https://api.xurrent.com/v1/requests/70384
```

```
status: 200 OK
```

```
{"id":70384,"status":"completed","service_instance":{"name":"Time Off Request Production","id":97},"team":{"name":"Service Desk","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":2},"member":{"name":"Krish Hanuang","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":16}}
```

*Not all request fields are shown above to keep the example simple.*

### Source ID

When references to resources with a Source ID are retrieved from the API, the `sourceID`
field will always be provided.

```
 $ curl -H "Authorization: Bearer <oauth-token>" https://api.xurrent.com/v1/requests?per_page=1
```

```
status: 200 OK
```

```
[{"subject":"NewRequest","category":"compliment","status":"assigned","sourceID":"N1C3AP1"}]
```

*Not all request fields are shown above to keep the example simple.*

See [source](../source.html) for more information on the usage of the `sourceID` field.

### Disabled

In case a referenced resource is disabled, the `disabled: true` property will be provided. When a referenced resource
is enabled, the `disabled` property is omitted.

```
 $ curl -H "Authorization: Bearer <oauth-token>" https://api.xurrent.com/v1/services/23
```

```
status: 200 OK
```

```
{"id":23,"name":"Short Term Production Planner","created_at":"2016-03-10T02:05:27-06:00","updated_at":"2016-03-10T02:10:51-06:00","sourceID":null,"support_team":{"name":"Application Development","id":7},"provider":{"name":"Widget Data Center, External IT","id":30,"disabled":true}}
```

## Attachments

Various rich text fields in Xurrent can hold attachments.
They may contain inline image or video files, and some of them can have attachments listed externally, in which case in the Xurrent UI these are displayed at the bottom of the text represented with a paperclip in front of each attachment.

Adding attachments and inline image or video files to rich text fields is a three-step process:

1. Get access to the Xurrent storage facility
2. Upload the files
3. Add references to the uploaded files to a rich text field

These steps are explained in more detail hereunder for a scenario where a request is created with an attachment linked to the first note.
For this example you will need a [Personal Access Token](../../index.html#personal-access-tokens) with Create access to Requests.

**Tip**: Using the one of the Xurrent API clients (SDKs) can make the process to upload attachments easier. The SDKs have specialized functionality to facilitate the steps described below. Please see the relevant documentation of the [SDK for ruby](https://github.com/code4me/4me-sdk-ruby#attachments) or the [.Net SDK](https://github.com/code4me/4me-sdk-csharp#upload-an-attachment) for more details.

Remarks:

- Depending on your environment (Windows or UNIX), the syntax of the curl commands hereunder will be slightly different. On a UNIX system, you need to escape the `$` sign like `-F "key=attachments/5/.../\${filename}" \`. On a Windows system you need to remove the backslash `\` at the end of each line, use double quotes, and escape any quotes within the double quotes.

**Step 1. Get access to the Xurrent storage facility**

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: <accountID>" \
 -X GET \
 "https://api.xurrent.com/v1/attachments/storage"
```

The response will contain the storage upload details:

```
status: 200 OK
```

```
{"size_limit":2147483648,"allowed_extensions":["csv","gif","png","log","pdf"],"provider":"s3","upload_uri":"https://xurrent.s3-accelerate.dualstack.amazonaws.com/","s3":{"acl":"private","key":"attachments/5/.../${filename}","policy":"eyJ...V19","success_action_status":201,"x-amz-algorithm":"AWS4-HMAC-SHA256","x-amz-credential":"AKIA...aws4_request","x-amz-date":"20201115T000000Z","x-amz-server-side-encryption":"AES256","x-amz-signature":"5a0...ae5"}}
```

In an on-premise environment the storage upload details might look like this instead:

```
status: 200 OK
```

```
{"size_limit":20971520,"allowed_extensions":["csv","gif","png","log","pdf"],"provider":"local","upload_uri":"https://api.example.com/v1/attachments","local":{"key":"attachments/5/.../${filename}","X-Xurrent-expiration":"2020-11-30T02:18:17Z","X-Xurrent-signature":"6dd...d0f"}}
```

**Step 2. Upload the files**

Upload the actual file(s) to the Xurrent storage facility. Post the file(s) to the value presented in upload\_uri, and post all parameter presented in the `s3` or `local` scope, preceded by the Content-Type of the file, and provide the file data last. For example:

```
 $ curl -F "Content-Type=plain/text" \
 -F "acl=private" \
 -F "key=attachments/5/.../\${filename}" \
 -F "policy=eyJ...V19" \
 -F "success_action_status=201" \
 -F "x-amz-algorithm=AWS4-HMAC-SHA256" \
 -F "x-amz-credential=AKIA...aws4_request" \
 -F "x-amz-date=20201115T000000Z" \
 -F "x-amz-server-side-encryption=AES256" \
 -F "x-amz-signature=5a0...ae5" \
 -F "file=@helloworld.txt" \
 "https://xurrent.s3-accelerate.dualstack.amazonaws.com/"
```

Or, in an on-premise environment:

```
 $ curl -H "Authorization: Bearer <token>" \
 -H "X-Xurrent-Account: <accountID>" \
 -F "Content-Type=plain/text" \
 -F "key=attachments/5/.../\${filename}" \
 -F "X-Xurrent-expiration=2020-11-30T02:18:17Z" \
 -F "X-Xurrent-signature=6dd...d0f" \
 -F "file=@helloworld.txt" \
 "https://api.example.com/v1/attachments"
```

Remarks:

- cURL interprets `-F “file=@...”` and reads the `helloworld.txt` from your disk (located in the directory where curl is executed) and sends it as form-encoded data to the server.
- The response in the s3 scope needs some reformatting to be used in a curl statement. Remove the comma `,` between parameters and make sure the parameters are preceded by `-F`. The parameter is formatted as `"attribute=value"` instead of `"attribute": "value"`. Make sure to format `"success_action_status": 201`, as `-F "success_action_status=201"`.

The response from the above command might look like this:

```
status: 201 Created
```

```
 <?xml version="1.0"?>
 <PostResponse>
 <Location>https://xurrent.s3-accelerate.dualstack.amazonaws.com/attachments%2F5%2F2020%2F11%2F15%2F6%2F1605413834-431xxxc1be%%2Fhelloworld.txt</Location>
 <Bucket>Xurrent</Bucket>
 <Key>attachments/5/2020/11/15/6/1605413834-431xxxcc1be/helloworld.txt</Key>
 <ETag>"9008d115b2d05a7ca6b495fd0cb998df"</ETag>
 </PostResponse>
```

Or, in an on-premise environment:

```
status: 200 OK
```

```
{"key":"attachments/5/.../helloworld.txt"}
```

**Step 3. Add references to the uploaded files to a note**

Create the new request and add all attachments in the `note_attachments` parameter:

```
 $ curl -H "Authorization: Bearer <token>" \
 -H "X-Xurrent-Account: <accountID>" \
 -X POST \
 -d '{
 "requested_for_id": 51,
 "subject": "Test",
 "category": "other",
 "note": "Attachment test",
 "note_attachments": [ {"key": "attachments/5/.../helloworld.txt", "filesize": "16"} ]
 }' \
 "https://api.xurrent.com/v1/requests"
```

Remarks:

- The value of `key` that is passed into the notes\_attachments parameter should match the string from the `<Key>...</Key>` XML response. In an on-premise environment it should match the value `key` that was in the JSON response.
- The `filesize` parameter is optional.
- You will need to add the other parameters for creating a valid Request, such as `requested_for_id` and `category`, see [Create a Request](../../requests.html#create-a-request).

### Inline attachments

To add an inline attachment to a rich text field the same process as described above is followed, except in the last step the attachment needs to be marked as `inline`, and a reference needs to be added within the rich text field using the special markdown syntax: `![](<key>)`. For example:

```
 $ curl -H "Authorization: Bearer <token>" \
 -H "X-Xurrent-Account: <accountID>" \
 -X POST \
 -d '{
 "requested_for_id": 51,
 "subject": "Test",
 "category": "other",
 "note_attachments": [ {"key": "attachments/5/.../helloworld.txt", "inline": true, "filesize": "16"} ],
 "note": "This is an inline attachment ![](attachments/5/.../helloworld.txt)"
 }' \
 "https://api.xurrent.com/v1/requests"
```

### Removing an attachment

To remove an attachment from a field, use the `_destroy` attribute.

For example, suppose that the `information` field of person `123` has an attachment with key `attachments/5/.../helloworld.txt`. To remove it, execute the following:

```
 $ curl -H "Authorization: Bearer <token>" \
 -H "X-Xurrent-Account: <accountID>" \
 -X PATCH \
 -d '{
 "information_attachments": [ {"key": "attachments/5/.../helloworld.txt", "_destroy": true } ]
 }' \
 "https://api.xurrent.com/v1/people/123"
```
