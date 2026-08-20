# Events API

The Events API is typically used by monitoring tools to create or update requests in Xurrent based on events. It is also possible for monitoring tools to use the [Mail API](../mail.html) to register new requests.

- [Submit Event](../events.html#submit-event)
 - [Response Request created](../events.html#response-request-created)
- [Default values](../events.html#default-values)
 - [Source](../events.html#source)
- [Parameters](../events.html#parameters)
 - [Configuration Item](../events.html#configuration-item)
- [Event matching](../events.html#event-matching)

## Submit Event

```
POST /events?subject=Server%20Down&source=MyMonitoringTool&sourceID=882395&note=Not%20reachable
```

When posting an event [these parameters](../events.html#parameters) are available. For most of the required [request fields](../../requests.html#fields) the Events API uses [default values](../events.html#default-values) in case a value is not specified.

### Response Request created

If a new request is created based for a given event, the following response is returned.

```
status: 201 Created
```

```
{"service_instance":{"name":"Data Center Rack Space","id":29},"organization":{"id":44,"name":"Widget Data Center, External IT"},"completion_reason":"solved","closure_code":"hardware_issue_resolved","completed_at":"2014-03-04T02:14:00-06:00","desired_completion_at":"2014-03-04T03:00:00-06:00","requested_by":{"name":"Patrick Spratt","id":56},"created_by":{"name":"Patrick Spratt","id":56},"created_at":"2009-02-02T12:18:00-06:00","category":"rfc","sourceID":null,"downtime_start_at":null,"updated_at":"2016-03-14T03:14:13-06:00","supplier":null,"resolution_target_at":null,"requester_resolution_target_at":null,"new_assignment":false,"grouping":"none","grouped_into":null,"member":{"name":"Carla Cluster","id":54},"resolution_duration":null,"supplier_requestID":null,"subject":"Add new rack in data center","response_target_at":null,"id":68673,"requested_for":{"name":"Patrick Spratt","id":56},"problem":null,"workflow":{"id":238,"subject":"Install new rack"},"project":null,"ci":null,"downtime_end_at":null,"impact":null,"team":{"name":"Unix Servers","id":13},"status":"completed","source":"4me Self Service","next_target_at":"no_target","template":null,"custom_fields":null,"waiting_until":null,"reviewed":true,"satisfaction":"satisfied","knowledge_article":null,"urgent":false,"addressed":false,"feedback":{"requested_by":{"satisfied_url":"https://widget.xurrent.com/requests/68673/2sii015q/149/yes","dissatisfied_url":"https://widget.xurrent.com/requests/68673/2sii015q/149/no"}}}
```

## Default values

To simplify request creation by system management or monitoring tools, default values are used when values have not been provided for [request fields](../../requests.html#fields) that are required.

category
: Set to `incident` if a service instance is to be related to the request. Otherwise, set to `other`.

created\_by
: Set to the current user

impact
: Set to `top` if category is `incident`. Otherwise the Impact field of the request is left empty.

member
: Set to the current user if a valid member is not provided and a status is specified that causes the Member field of the request to be required. When the `template_id` parameter is used and the request template is linked to a workflow template, then the Member field of the request is set to the manager of the workflow.

requested\_by
: Set to the current user

requested\_for
: Set to the requested\_by

service\_instance
: Set to the first service instance of the configuration item when a configuration item is specified for the request.

source
: Set to `Event`.

status
: Set to `assigned`. When the `template_id` parameter is used and the request template is linked to a workflow template, then set to `workflow_pending`.

team
: The team to which the person specified as the `member` belongs. Otherwise, if a service instance is to be related to the request, the First Line Team of this service instance or, if a First Line Team is not specified or the current user is a member of the First Line Team or the Support Team, the Support Team of this service instance. Else, set to the Service Desk Team of the first line support agreement that covers the account of the person selected in the Requested for field.
: Note: if an invalid team was specified in the API call, the default team is selected in the request.

Relying on all default values makes it possible to create a request by providing only the `subject` field. It is recommended, though, to always specify the [source](../events.html#source), [note](../events.html#response-request-updated) and [configuration item](../events.html#configuration-item) when possible.

### Source

When creating a new request using the Events API, the [source](../../general/source.html) of the new request is set to `event` by default.
It is best practice, however, to always specify the name of the monitoring tool that passed the event to Xurrent as the source.

This also improves the [matching of events](../events.html#event-matching) in case multiple system management tools monitor the same [Configuration Items](../../configuration_items/index.html).

## Parameters

The following parameters can be used in an Events API call to set the field values of the request:

category
: Used to specify an option in the Category field of the request. The available field options can be found in the [Fields](../../requests.html#fields) section of the Requests API page.

ci
: Used to specify the configuration item that is to be related to the request. The configuration item needs to be identified by its label or, in case of a software CI, its Name field value.

ci\_id
: Used to specify the configuration item that is to be related to the request. The configuration item needs to be identified by its ID.

ci\_source
: Used together with the `ci_sourceID` parameter to specify the configuration item that is to be related to the request. This parameter should be used to specify the configuration item’s Source field value.

ci\_sourceID
: Used together with the optional `ci_source` parameter to specify the configuration item that is to be related to the request. The configuration item needs to be defined using its Source ID field value.

completion\_reason
: Used to specify an option in the Completion reason field of the request when its Status field is set to ‘completed’. The available field options can be found in the [Fields](../../requests.html#fields) section of the Requests API page.

desired\_completion\_at
: Used to specify the date and time that has been agreed on for the completion of the request. The desired completion overwrites the automatically calculated resolution target of any affected SLA that is related to the request when the desired completion is later than the affected SLA’s resolution target. By default, the `requested_by` receives a notification based on the ‘Desired Completion Set for Request’ email template whenever the `desired_completion_at` is set, updated or removed.

downtime\_end\_at
: Used to specify the end date and time of a service outage. Be sure to use the correct [datetime format](../../general/data_types.html).

downtime\_start\_at
: Used to specify the start date and time of a service outage. Be sure to use the correct [datetime format](../../general/data_types.html).

impact
: Used to specify an option in the Impact field of the request. The available field options can be found in the [Fields](../../requests.html#fields) section of the Requests API page.

internal\_note
: Used to provide the text that needs to be added as an Internal Note to the request. Be sure to apply [URL encoding](http://en.wikipedia.org/wiki/Percent-encoding) for a valid URI syntax when, for example, spaces are included in the text.

member
: Used to specify the person to which the request is to be assigned. This person needs to be identified by the Person record’s Primary email field value.

member\_id
: Used to specify the person to which the request is to be assigned. This person needs to be identified by the Person record’s ID.

note
: Used to provide the text that needs to be added as a Note to the request. Be sure to apply [URL encoding](http://en.wikipedia.org/wiki/Percent-encoding) for a valid URI syntax when, for example, spaces are included in the text.

problem\_id
: Used to specify the problem that is to be related to the request. The problem needs to be identified by its ID.

requested\_by
: Used to specify the person who is to be selected in the Requested by field of the request. This person needs to be identified by the Person record’s Primary email field value.

requested\_by\_id
: Used to specify the person who is to be selected in the Requested by field of the request. This person needs to be identified by the Person record’s ID.

requested\_for
: Used to specify the person who is to be selected in the Requested for field of the request. This person needs to be identified by the Person record’s Primary email field value.

requested\_for\_id
: Used to specify the person who is to be selected in the Requested for field of the request. This person needs to be identified by the Person record’s ID.

service\_instance
: Used to specify the service instance that is to be related to the request. The service instance needs to be identified by its Name field value.

service\_instance\_id
: Used to specify the service instance that is to be related to the request. The service instance needs to be identified by its ID.

source
: Used to specify the name of the monitoring tool, see [source](../../general/source.html). After the request has been created, this value is visible in its Audit Trail.

sourceID
: Used to specify the unique ID of the event for which the request is to be registered, see [source](../../general/source.html). After the request has been created, this value is visible in its Audit Trail.

status
: Used to specify an option in the Status field of the request. The available field options can be found in the [Fields](../../requests.html#fields) section of the Requests API page.

subject
: Used to specify the Subject of the request. Be sure to apply [URL encoding](http://en.wikipedia.org/wiki/Percent-encoding) for a valid URI syntax when, for example, spaces are included in the text.

supplier
: Used to specify the Organization to which the request has been submitted. The Organization needs to be identified by its Name field value.

supplier\_id
: Used to specify the Organization to which the request has been submitted. The Organization needs to be identified by its ID.

supplier\_requestID
: Used to specify the identifier under which the request has been registered at the supplier organization.

support\_domain
: Used to specify the support domain account ID in which the request is to be registered. This parameter needs to be specified when the current user’s Person record is registered in a directory account. The ID of a Xurrent account can be found in the ‘Account Overview’ section of the Settings console.

team
: Used to specify the team to which the request is to be assigned. The team needs to be identified by its Name field value.

team\_id
: Used to specify the team to which the request is to be assigned. The team needs to be identified by its ID.

template\_id
: Used to specify the request template that is to be applied to the request. This request template needs to be identified by its ID. It is important to note that the field values specified in the API call overwrite the values specified in the request template.

waiting\_until
: Used to specify the date and time at which the status of the request is to be updated from `waiting_for` to `assigned`. Be sure to use the correct [datetime format](../../general/data_types.html).

workflow\_id
: Used to specify the workflow that is to be related to the request. The workflow needs to be identified by its ID.

### Configuration Item

When creating new requests, the `ci_id` parameter defines the reference to a configuration item. In most cases, however, monitoring tools will not know the ID of the configuration item by which it is known in Xurrent. So a separate call to the Xurrent API would be needed to fetch the `ci_id` based on the `source` and `sourceID` of the configuration item.

To simplify the CI selection, the [Events API](../events.html#submit-event) accepts the `ci` parameter so that that the value in the CI’s Label field can be used to find the CI in Xurrent.

The combination of the `ci_source` (optional) and `ci_sourceID` parameters can also be used to identify the CI that is to be related to the request. This can be useful, for instance, when a discovery tool registered the CI in Xurrent and entered a value in its `source` and `sourceID` fields. Example:

```
POST /events?subject=Server%20Down&source=MyMonitoringTool&sourceID=12345&ci_source=MyDiscoveryTool&ci_sourceID=56789
```

## Event matching

If an event is submitted within 24 hours of the creation of an existing open request that has the same `source`, `service_instance`, and `ci` parameters, then a new request does *not* get generated. Instead the `note` parameter is used to add a new note to the existing request. To avoid duplicate notes, however, the note is only added when its text is different from a previous note of the existing request. If the `note` parameter is the same as a previous note, or if the `note` parameter is not provided, then no changes are made to the existing request.

If an existing request is updated for a given event, the following parameters can be used to make changes to the existing request:

`completion_reason` `desired_completion_at` `downtime_start_at` `downtime_end_at` `status` `waiting_until` `team` `team_id` `member` `member_id`

If an existing request is updated for a given event, the following response is returned.

```
status: 200 OK
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](../../requests.html#fields) of the updated request and is similar to the response in [Response Request created](../events.html#response-request-created)

When the `service_instance` parameter is not included in the event, it is found by looking up the service instance to which the configuration item is linked. Once the service instance is known, the event matching starts.

When the `ci` parameter is not included in the event, event matching will not prevent the generation of a new request unless the `subject` and `note` parameters, as well as the `account`, `source`, and `requested_for` parameters are the same as those of an existing open request that was generated within the past 24 hours.
