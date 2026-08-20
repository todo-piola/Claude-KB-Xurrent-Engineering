# Short URLs API

- [List short URLs](index.html#list-short-urls)
- [Get a single short URL](index.html#get-a-single-short-url)
- [Get a QR code image](index.html#get-a-qr-code-image)
- [Create a short URL](index.html#create-a-short-url)
- [Update a short URL](index.html#update-a-short-url)
- [Fields](index.html#fields)
- [Reserving multiple short URLs](index.html#reserving-multiple-short-urls)

## List short URLs

List all short URLs for an account:

```
GET /short_urls
```

### Response

```
status: 200 OK
```

```
[{"id":68875,"short_url":"https://itrp.io/XaeLN9","uri":"itrp:self_service?ci_id=31429","created_at":"2015-11-19T14:45:52-08:00","updated_at":"2015-11-19T14:45:52-08:00"},{"id":68874,"short_url":"https://itrp.io/EZCV9H","uri":"itrp:self_service?request_template_id=5823","created_at":"2015-11-19T14:45:52-08:00","updated_at":"2015-11-19T14:45:52-08:00"},{"id":68876,"short_url":"https://itrp.io/77gegn","uri":"https://4me.com","created_at":"2015-11-19T14:47:33-08:00","updated_at":"2015-11-19T14:47:33-08:00"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of short URLs.

### Collection Fields

By default the following fields will appear in collections of short URLs:

`id` `sourceID` `name` `group` `rule_set` `reference` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `created_at` `updated_at`

### Sorting

By default a collection of short URLs is sorted **descending** by `id`.

## Get a single short URL

```
GET /short_urls/:id
```

### Response

```
status: 200 OK
```

```
{"id":68875,"short_url":"https://itrp.io/XaeLN9","uri":"itrp:self_service?ci_id=31429","created_at":"2015-11-19T14:45:52-08:00","updated_at":"2015-11-19T14:45:52-08:00"}
```

The response contains [these fields](index.html#fields).

## Get a QR code image

```
GET /short_urls/:short_url_token/qrcode
```

This returns a chunked PNG.

The following HTML example shows how the QR code of a short URL can be included dynamically in a web page (place the HTML between angle brackets):

```
 img src="https://api.xurrent.com/v1/short_urls/dUD3Rb/qrcode"
```

The example below shows how the QR code of a short URL can be downloaded as a PNG image file with the name `filename.png`:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X GET \
 https://api.xurrent.com/v1/short_urls/dUD3Rb/qrcode > filename.png
```

## Create a short URL

```
POST /short_urls
```

When creating a new short URL [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created short URL and is similar to the response in [Get a single short URL](index.html#get-a-single-short-url)

The following are two simple examples for creating a short URL using CURL:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X POST \
 https://api.xurrent.com/short_urls?twitter_name=Xurrent
```

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X POST \
 https://api.xurrent.com/short_urls?plain_text=hello%20world%21
```

## Update a short URL

```
PATCH /short_urls/:id
```

When updating a short URL [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated short URL and is similar to the response in [Get a single short URL](index.html#get-a-single-product-category)

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the short URL was created.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the short URL.

short\_url
: *Readonly* **[string](../general/data_types.html) (max 255)** — The Short Url field contains the automatically generated website address that is forwarded to URI.

uri
: *Optional* **[string](../general/data_types.html) (max 4096)** — The URI field contains the uniform resource identifier to which the short URL is forwarded.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the short URL. If the short URL has no updates it contains the `created_at` value.

### Additional fields

The following are additional fields that can be used to automatically generate the `uri` value of a short URL:

ci\_id
: *Optional* **[reference](../general/data_types.html#references) to [Configuration Item](../configuration_items/index.html)** — The Configuration item field is used to select the CI for which a request is to be registered in Xurrent Self Service when the short URL is used.

email\_body
: *Optional* **[string](../general/data_types.html)** — The Body field is used to enter the body of the email that is to be generated when the short URL is used. This field should only be used in conjunction with the ‘email\_to’ and ‘email\_subject’ fields.

email\_subject
: *Optional* **[string](../general/data_types.html)** — The Subject field is used to enter the subject of the email that is to be generated when the short URL is used. This field should only be used in conjunction with the ‘email\_to’ and ‘email\_body’ fields.

email\_to
: *Optional* **[string](../general/data_types.html)** — The To field is used to enter the email address of the recipient of the email that is to be generated when the short URL is used. This field should only be used in conjunction with the ‘email\_subject’ and ‘email\_body’ fields.

geo\_latitude
: *Optional* **[string](../general/data_types.html)** — The Latitude field is used to enter the latitude coordinate of the location for which a map should be opened when the short URL is used. This field should only be used in conjunction with the ‘geo\_longitude’ field.

geo\_longitude
: *Optional* **[string](../general/data_types.html)** — The Longitude field is used to enter the longitude coordinate of the location for which a map should be opened when the short URL is used. This field should only be used in conjunction with the ‘geo\_latitude’ field.

knowledge\_article\_id
: *Optional* **[reference](../general/data_types.html#references) to [Knowledge Article](https://developer.xurrent.com/v1/knowledge_article/)** — The Knowledge Article field is used to select the knowledge article which instructions need to be displayed when the short URL is used in Xurrent Self Service.

map\_address
: *Optional* **[string](../general/data_types.html)** — The Address field is used to enter the address (or only the city or country) for which a map should be opened when the short URL is used.

plain\_text
: *Optional* **[string](../general/data_types.html)** — The Plain text field is used to enter the text that should be displayed when the short URL is used.

request\_template\_id
: *Optional* **[reference](../general/data_types.html#references) to [Request Template](../task_templates.html)** — The Request template field is used to select the request template that is to be applied to each new request that is opened when in Xurrent Self Service when the short URL is used.

skype\_name
: *Optional* **[string](../general/data_types.html)** — The Skype username field is used to enter the Skype name that is to be called when the short URL is used.

sms\_tel
: *Optional* **[string](../general/data_types.html)** — The Telephone number field is used to enter the telephone number of the recipient of the SMS message that is to be generated when the short URL is used. This field should only be used in conjunction with the ‘sms\_body’ field.

sms\_body
: *Optional* **[string](../general/data_types.html)** — The SMS message field is used to enter the text of the SMS message that is to be generated when the short URL is used. This field should only be used in conjunction with the ‘sms\_tel’ field.

tel
: *Optional* **[string](../general/data_types.html)** — The Telephone number field is used to enter the telephone number that is to be called when the short URL is used.

tweet
: *Optional* **[string](../general/data_types.html)** — The Tweet field is used to enter the text of the Twitter tweet that is to be generated when the short URL is used.

twitter\_name
: *Optional* **[string](../general/data_types.html)** — The Twitter username field is used to enter the name of the Twitter user whose Twitter feed is to be opened when the short URL is used.

website\_url
: *Optional* **[string](../general/data_types.html)** — The Website URL field is used to enter the uniform resource locator of a website to which the short URL is to forward when it is used.

## Reserving multiple short URLs

Multiple short URLs can be generated in bulk using the following API call:

```
$ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X POST \
 https://api.xurrent.com/v1/short_urls/reserve?amount=1000
```

The example above generates 1000 short URLs without a URI. Once these short URLs have been generated, they are reserved for the account. These reserved URLs can then be exported and used to order QR codes or NFC tags in bulk.

The response from the API is a token that acts as the unique identifier for the job. This token can be used to retrieve [information about the progress](index.html#job-progress) of the job.

```
status: 200 OK
```

```
{"token":"69ea3...1e7133"}
```

It is important to note that the API user needs to have the Configuration Manager or Account Administrator role to be able to reserve short URLs using the API. In the example above, the API user specifically needs to have the Configuration Manager or Account Administrator role of the account which `id` is “wdc”. The [Authentication section](../index.html#authentication) describes how the `api-token` of the API user can be found.

In the example above it would not be necessary to specify `-H "X-Xurrent-Account: wdc"` provided that the Person record of the API user is registered in the account which `id` is “wdc”.

### Parameter

The following parameter is supported:

amount
: *Required* **[integer](../general/data_types.html)** — The number of short URLs that are to be generated for the account. A maximum of 10,000 can be reserved at any time per account.

## Job progress

The reservation process runs as a background job. It is possible to check the progress of a job automatically using the token received from the job response.

Five minutes after the job is completed, the progress information is not available anymore through the API.

Example:

```
$ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X GET
 https://api.xurrent.com/v1/short_urls/reserve/69ea3...1e7133
```

Depending on the state of the job, one of the following responses is returned:

### Queued

```
status: 200 OK
```

```
{"state":"queued"}
```

The job is scheduled for execution.

### Processing

```
status: 200 OK
```

```
{"state":"processing","message":"Reserved 700 Short URLs"}
```

The job is being processed.

### Done

```
status: 200 OK
```

```
{"state":"done"}
```

The job is complete.

Note that if the process was able to recover from an error, the state `done` is returned. The response contains the state `error` as outlined below only when an error prevented the job from completing.

### Error

```
status: 200 OK
```

```
{"state":"error","message":"..."}
```

The job was aborted prematurely because of an unrecoverable error. A short description of the issue is provided in the `message` attribute. More detailed information can be found in the [Job Log](index.html#job-log). Errors should always be investigated.

### Not Found

```
status: 404 Not Found
```

The job was completed more than 5 minutes ago, so no progress information is available anymore. Information on the completed job can still be found in the [Job Log](index.html#job-log).

## Job log

Each job that is complete (with or without errors) is entered in the *System Logs* of the *Settings* console. Log into Xurrent as an Account Administrator and go to *Settings* => *System Logs* and select the *Job Log* view to see them all.

The `Level` column will contain `Fatal` in case an [error](index.html#error) has occurred.
