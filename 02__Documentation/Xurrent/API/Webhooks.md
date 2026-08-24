# Webhooks

Webhooks are used by organizations to keep other applications in sync with their Xurrent accounts. Scripts that are published on public web servers (i.e. servers that can be accessed from the internet) can be called by webhooks in near real-time to collect data from Xurrent and to use this data to update an external application or to perform an update in Xurrent itself.

## What Are Webhooks?

Webhooks are a way to tell Xurrent to call a script on a web server whenever a given event occurs in Xurrent. A script is typically developed to execute specific actions for an organization that uses Xurrent. The organization for which such a script was developed normally hosts it on one of its own web servers.

Some possible uses for webhooks include:

- Notify an IM client or mobile device.
- Collect data for data warehousing and/or dashboards.
- Synchronize data between two systems.

## Registering Webhooks

Webhooks can be created in an organization’s Xurrent account by going to *Settings* → *Webhooks* in the Xurrent application, or with the [Xurrent Webhooks API](events.html).

Select the event that needs to be listened to from the select box, and enter the URI that needs to receive the call from the webhook.

Once a webhook has been registered and [verified](../webhooks.html#verification), Xurrent issues an HTTP POST call to the URI specified in the webhook every time the selected event occurs.

Webhooks are asynchronous events. They are sent near real-time. Sometimes there can be a small delay.

Xurrent calls the specified URI every time the event happens (unless this is via import). This means that if, for example, 1,000 tasks are created via the API, the webhook is called 1,000 times if its selected event is `task.create`. Contrary to this, a CSV import of a 1,000 tasks does not cause a single call to that same webhook.

## Verification

In order to ensure that you are the true owner of the endpoint defined in the webhook URI field a verification step is necessary.

When a webhook is first registered Xurrent will immediately send a `webhook.verify` webhook to the URI endpoint defined in that webhook.

The `payload` contains a `callback` parameter that must be called to prove you are the true owner of the URI defined in the webhook:

```
POST /mywebhook HTTP/1.1
Content-Type: application/json; charset=utf-8
Host: myserver.example.com
User-Agent: 4me/1.0 (https://developer.xurrent.com/v1/webhooks)
Link: <https://mycompany.xurrent.com/webhooks/219>; rel="canonical",
 <https://api.xurrent.com/v1/webhooks/219>; rel="resource"
```

```
{"webhook_id":219,"webhook_nodeID":"NG1lMjQuMjIwODEyMTAxMzQ1QDRtZS1kZW1vLmNvbS9XZWJob29rLzM","account":"https://mycompany.xurrent.com","name":"Note added to Request of mycompany","event":"webhook.verify","object_id":219,"object_nodeID":"NG1lMjQuMjIwODEyMTAxMzQ1QDRtZS1kZW1vLmNvbS9XZWJob29rLzM","person_id":8543,"person_nodeID":"NG1lMjQuMjIwODEyMTAxMzQ1QDRtZS1kZW1vLmNvbS9QZXJzb24vNg","person_name":"Howard Tanner","payload":{"callback":"https://mycompany.xurrent.com/webhooks/219/verify?code=EmzqeGYTj5LAIwY-hWoYNLJQ&expires_at=1610618451"}}
```

For manual verification simply paste the `callback` URL in your favourite web browser.

For automated verification make sure the server that receives the `webhook.verify` message sends a GET or POST request to the `callback` URL:

```
$ curl -v https://mycompany.xurrent.com/webhooks/219/verify?code=EmzqeGYTj5LAIwY-hWoYNLJQ&expires_at=1610618451
```

Before calling the `callback` URL, it is recommended to verify [the authenticity of the webhook](../webhooks.html#verifying-the-authenticity-of-a-webhook). Verify the webhook request you receive is in fact originating from your Xurrent account and that the contents are what you expect.

When another webhook with the exact same `URI` was already verified in your Xurrent account the verification step will not be initiated again when subsequent webhooks are created.

If you create a webhook before the server is ready to receive the `webhook.verify` message, it is possible to resend the verification code from the GUI within 24 hours.
When an unverified webhook is updated a new `webhook.verify` message is send with a fresh verification code that is valid again for 24 hours. The old verification callback URL is then no longer valid.

Note that if the URI of a webhook is updated it needs to be verified again. The webhook will be inactive until the verification callback is received by Xurrent.
Of course it is possible to define a new webhook first and delete the old webhook once the new one has been verified to ensure no events are missed.

## Webhook Contents

Webhooks are sent as HTTP POST calls to URIs with a JSON body (with `Content-Type: application/json`) for easy parsing in almost any programming language. Webhook callback bodies can contain the following parameters:

webhook\_id
: The identifier of the webhook registered in Xurrent.

webhook\_nodeID
: The [GraphQL identifier](https://developer.xurrent.com/graphql/#global-node-ids) of the webhook registered in Xurrent.

account\_id
: The account ID of your organization’s Xurrent account.

account
: The url of your organization’s Xurrent account.

custom\_url
: The custom url of your organization’s Xurrent account, if defined.

name
: The name of the webhook that got fired.

event
: The event of the webhook that got fired.

object\_id
: The identifier of the Xurrent record that triggered the event. Use this identifier to make a Xurrent API call to retrieve further details if needed.

object\_nodeID
: The [GraphQL identifier](https://developer.xurrent.com/graphql/#global-node-ids) of the Xurrent record that triggered the event. Use this identifier to make a Xurrent API call to retrieve further details if needed.

openid\_connect\_discovery
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether the webhook for this app uses OpenID Connect Discovery to allow retrieval of the policy’s public key via a JWKS endpoint.

person\_id
: The identifier of the person that triggered the event. This field is empty if the trigger was caused by a system event.

person\_nodeID
: The [GraphQL identifier](https://developer.xurrent.com/graphql/#global-node-ids) of the person that triggered the event. This field is empty if the trigger was caused by a system event.

person\_name
: The name of the person that triggered the event. This field is empty if the trigger was caused by a system event.

payload[audit\_line\_id]
: The identifier of the audit entry that Xurrent generated for the creation or update of the Xurrent record that triggered the event. This parameter is included only when the event caused an audit entry to be generated. The addition of a note, or specifying a value in the Time spent field, does not cause an audit entry to get generated.

payload[audit\_line\_nodeID]
: The [GraphQL identifier](https://developer.xurrent.com/graphql/#global-node-ids) of the audit entry that Xurrent generated for the creation or update of the Xurrent record that triggered the event. This parameter is included only when the event caused an audit entry to be generated. The addition of a note, or specifying a value in the Time spent field, does not cause an audit entry to get generated.

payload[note\_id]
: The identifier of the note record that was created during the creation or update of the Xurrent record that triggered the event. This parameter is included only when a note was created during the creation or update of the Xurrent record that triggered the event.

payload[note\_nodeID]
: The [GraphQL identifier](https://developer.xurrent.com/graphql/#global-node-ids) of the note record that was created during the creation or update of the Xurrent record that triggered the event. This parameter is included only when a note was created during the creation or update of the Xurrent record that triggered the event.

payload[source]
: The source of the Xurrent record that triggered the event. This parameter is not included if the Source field of the Xurrent record that triggered the event does not contain a value.

payload[sourceID]
: The source ID of the Xurrent record that triggered the event. This parameter is not included if the Source ID field of the Xurrent record that triggered the event does not contain a value.

payload[status]
: The status of the Xurrent record that triggered the event. This parameter is not included if the Xurrent record that triggered the event does not have a Status field.

payload[previous\_status]
: The status of the Xurrent record before its status was updated, causing the event to be triggered. This parameter is included only for the events request.status-changed, problem.status-changed, workflow.status-changed, task.status-changed, project.status-changed and project\_task.status-changed.

payload[team][id]
: The identifier of the team that is linked to the Xurrent record that triggered the event. This parameter is not included if the type of Xurrent record that triggered the event cannot be assigned to a team.

payload[team][nodeID]
: The [GraphQL identifier](https://developer.xurrent.com/graphql/#global-node-ids) of the team that is linked to the Xurrent record that triggered the event. This parameter is not included if the type of Xurrent record that triggered the event cannot be assigned to a team.

payload[team][name]
: The name of the team that is linked to the Xurrent record that triggered the event. This parameter is not included if the type of Xurrent record that triggered the event cannot be assigned to a team.

payload[team][sourceID]
: The source ID of the team that is linked to the Xurrent record that triggered the event. This parameter is not included if the Source ID field of this team does not contain a value.

payload[team][disabled]
: The Disabled checkbox value of the team that is linked to the Xurrent record that triggered the event. This parameter is not included if this team is enabled.

payload[team][account][id]
: The account ID of the team that is linked to the Xurrent record that triggered the event. This parameter is included whenever the Xurrent record that triggered the event can be assigned and has a value in its Team field.

payload[team][account][name]
: The name of the account of the team that is linked to the Xurrent record that triggered the event. This parameter is included whenever the Xurrent record that triggered the event can be assigned and has a value in its Team field.

payload[member][id]
: The identifier of the person who is selected in the Member field of the Xurrent record that triggered the event. This parameter is included whenever the Xurrent record that triggered the event has a value in its Member field.

payload[member][nodeID]
: The [GraphQL identifier](https://developer.xurrent.com/graphql/#global-node-ids) of the person who is selected in the Member field of the Xurrent record that triggered the event. This parameter is included whenever the Xurrent record that triggered the event has a value in its Member field.

payload[member][name]
: The name of the person who is selected in the Member field of the Xurrent record that triggered the event. This parameter is included whenever the Xurrent record that triggered the event has a value in its Member field.

payload[member][sourceID]
: The source ID of the person who is selected in the Member field of the Xurrent record that triggered the event. This parameter is not included if the Source ID field of this person does not contain a value.

payload[member][disabled]
: The Disabled checkbox value of the person who is selected in the Member field of the Xurrent record that triggered the event. This parameter is not included if this person is enabled.

payload[member][account][id]
: The account ID of the person who is selected in the Member field of the Xurrent record that triggered the event. This parameter is included whenever the Xurrent record that triggered the event has a value in its Member field.

payload[member][account][name]
: The name of the account of the person who is selected in the Member field of the Xurrent record that triggered the event. This parameter is included whenever the Xurrent record that triggered the event has a value in its Member field.

The payload for the following events contains additional information in their payload:

- **time\_entry.create**, **time\_entry.delete** or **time\_entry.update** will contain all fields of the time entry that triggered the event except `cost`, as described in [Time Entries API](../time_entries.html#fields)
- **out\_of\_office\_period.create**, **out\_of\_office\_period.delete** or **out\_of\_office\_period.update** will contain all fields of the out of office period that triggered the event, as described in [Out of Office Periods API](../out_of_office_periods.html#fields)
- **webhook.verify** will contain the `callback` parameter as described in [webhook verification](../webhooks.html#verification)

In addition references to URIs of interest are provided via the `Link` http header. The following relation types might be received:

canonical
: URI to the affected resource viewable via the Xurrent UI application.

resource
: URI to the affected resource viewable via the Xurrent API.

related
: URI to a related affected resource viewable via the Xurrent API. For example, if a note was added to a request, then this points to the note details. The link with relation type `resource` points to the request in this example.

### Request

```
POST /mywebhook HTTP/1.1
Content-Type: application/json; charset=utf-8
Host: myserver.example.com
User-Agent: 4me/1.0 (https://developer.xurrent.com/v1/webhooks)
Link: <https://mycompany.xurrent.com/requests/219>; rel="canonical",
 <https://api.xurrent.com/v1/requests/219>; rel="resource",
 <https://api.xurrent.com/v1/requests/219/notes/3455>; rel="related"
```

```
{"webhook_id":945,"account":"https://mycompany.xurrent.com","name":"Note added to Request of mycompany","event":"request.note-added","object_id":219,"person_id":8543,"person_name":"Howard Tanner","payload":{"source":"self service","member":{"name":"Tom Edwards","id":8529},"status":"workflow_pending","team":{"id":372,"name":"End-User Support, Houston"}}}
```

## Expected Response

**Note**: It is expected that the webhook service responds **immediately** to the webhook request.

Make sure the status code of the response is between 200 and 299 ( preferably 200 OK ) which indicates success. Xurrent simply discards the rest of the results of the webhook.

The webhook request to the web server on which the script is hosted times out after 10 seconds. Move long running processes (e.g. PDF generation) into an asynchronous background task and make sure that the script responds immediately to the Xurrent server.

## Failed Callbacks

If Xurrent receives anything other than a 2xx HTTP response code (likely meaning that the script has been moved, is non-existent, or misconfigured) or a request to the web server times out, Xurrent retries the HTTP POST call periodically. After several failures, the message is dropped and no further delivery attempts are made. Email notifications are sent out for these exceptions. By default, these exception notifications are sent to each person who has the Account Administrator role of the account in which the webhook is registered.

## Automatic Disabling

A webhook can be temporarily disabled. In addition, Xurrent automatically disables a webhook when there have been 20 consecutive failures for the exact same webhook over a period longer than a week. The details of the disabled webhook (viewable via the Xurrent application or via the [Webhooks API](events.html)) include the last error as received by Xurrent.

## Security and Privacy Considerations

As Xurrent needs to call a script on a server of a different organization via a publicly available connection, there is a potential vulnerability to hacks on that server.

- Make sure to verify the contents of a webhook callback as being authentic and un-tampered. See [Verifying the Authenticity of a Webhook](../webhooks.html#verifying-the-authenticity-of-a-webhook).
- Use the secure https protocol in the URI when possible.
- Be aware that scripts can obtain information from Xurrent that is potentially private.
- Read the [Webhooks Terms of Service](tos/index.html) carefully.

## Triggered Accounts

Sometimes webhooks will be triggered by Xurrent records registered in other accounts. For example when a Service Level Agreement registered in account `globalnet` is linked to a customer registered in the `wdc` account, `sla.update` webhooks for both accounts will be triggered when that Service Level Agreement is updated.

In general when a record is visible in the “All …” view, e.g. “All Service Level Agreements”, of an account then the webhooks will be triggered for that account.

## Verifying the Authenticity of a Webhook

In order to verify that a webhook request is in fact originating from your Xurrent account the webhook payload can be cryptographically signed. This is achieved by linking the webhook to a [Webhook Policy](../webhook_policies.html). Within the Xurrent application go to *Settings* → *Webhooks Policies*, and create a webhook policy choosing a preferred algorithm that will be used to cryptographically sign the webhook messages. When you receive a webhook request the payload will be a [JSON Web Token (JWT)](https://tools.ietf.org/html/rfc7519). Use the public key from the webhook policy to decode and verify the payload. The private key of the webhook policy is only known to Xurrent.

### Automatic Key Discovery

When a webhook has the `openid_connect_discovery` flag enabled and its webhook policy uses an asymmetric algorithm (RSA or ECDSA), the public key needed to verify the JWT can be discovered automatically using the [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) protocol. This eliminates the need to manually distribute or configure public keys.

When this feature is enabled, the JWT sent by the webhook will contain:

- An `iss` (issuer) claim that points to a discovery endpoint specific to the webhook policy, e.g. `https://mycompany.xurrent.com/webhook_policies/<policy-name>`.
- A `kid` (key ID) header that identifies the signing key.

To retrieve the public key:

1. Read the `iss` claim from the JWT payload.
2. Fetch the OpenID Connect Discovery document at `<iss>/.well-known/openid-configuration`. This document contains a `jwks_uri` field.
3. Fetch the JSON Web Key Set (JWKS) from the `jwks_uri`.
4. Find the key in the JWKS that matches the `kid` from the JWT header.

The discovery and JWKS endpoints are publicly accessible and do not require authentication. Responses are cacheable for up to 1 hour.

### Other Verification Mechanisms

Additional measures could include adding a secret query parameter to the URI, and then to have this parameter checked by your script.

In addition, it is possible to use basic http authentication by providing the username:password in the webhook URI, like this:

```
https://myuser:mylogin@myserver.example.com/mywebhook
```

Lastly, Xurrent always sends the identifier of the webhook as part of the response, which could also be used in a verification step. The identifier of a webhook can be found by selecting the webhook in the Xurrent application and looking at the number that is visible in the address bar of the browser, and/or via the [Xurrent Webhooks API](events.html).

## Testing Webhooks

Testing that a webhook works can be a bit of a challenge. Thanks to [Webhook Tester](http://webhook.site/) this has been made quite simple.

### Setting Up

First, be sure to have the Account Administrator role within the Xurrent application.

Then visit [Webhook Tester](http://webhook.site/) and copy the URL that is then shown in the header.

Within the Xurrent application go to *Settings* → *Webhooks*. Add a new Webhook, select for example “request.update” from the Event select box, and paste the URL from Webhook Tester into the URI field, and save this webhook.

### Verify the Webhook

Go back to [Webhook Tester](http://webhook.site/). You should have received a webhook request! At the “Raw Content” field be sure to check the field “Format JSON”. Then copy the `callback` URL from the payload, and paste this URL in a separate tab in your browser. You should then see the message “Verification successful”. The webhook is now successfully setup, and your webhook script is now ready to receive webhook requests.

### Testing the Webhook Is Fired

To test that the webhook fires simply create a request and update it. Check if the webhook fired by refreshing the page at [Webhook Tester](http://webhook.site/).

## Example Conversation

In the example below a webhook test is performed using the command line tool `curl`. This example shows how to [test a webhook](events.html#test-a-webhook) without actually modifying any data in Xurrent.

### Setting Up

First [create a webhook](events.html#create-a-webhook):

```
$ curl -v -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X POST \
 -d '{"event":"request.create", "uri":"https://webhook.site/abc/1"}' \
 https://api.xurrent.com/v1/webhooks/
```

```
status: 201 Created
Location: https://wdc.xurrent.com/webhooks/2
```

```
{"id":2,"name":"Request created in WDC","event":"request.create","uri":"http://requestb.in/nlety4nl","created_at":"2016-01-27T20:38:32-06:00","updated_at":"2016-01-27T20:38:32-06:00"}
```

Then [verify the webhook](../webhooks.html#verification).

And then [test the webhook](events.html#test-a-webhook) that was just created:

```
$ curl -v -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X POST
 https://api.xurrent.com/v1/webhooks/2/test
```

```
status: 204 No Content
```

Refresh the Webhook Tester page. It should show a new event posted for the event `request.create` that triggered the webhook with webhook\_id 2.
