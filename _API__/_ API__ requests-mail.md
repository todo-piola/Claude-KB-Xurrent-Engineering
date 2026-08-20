# Mail API

The Mail API can be used by end users and monitoring tools to submit requests by sending email to the email address of a service provider organization’s Xurrent account. It is also possible for monitoring tools to use the [Events API](../events.html) to register new requests.

- [Sending Email](../mail.html#sending-email)
 - [Mail from end users](../mail.html#mail-from-end-users)
 - [Mail from monitoring tools](../mail.html#mail-from-monitoring-tools)
- [Attachments](../mail.html#attachments)
- [Default values](../mail.html#default-values)
- [Parameters](../mail.html#parameters)
 - [Text formatting](../mail.html#text-formatting)
 - [Linking records of other accounts](../mail.html#linking-records-of-other-accounts)
- [Adding a note to an existing record](../mail.html#adding-a-note-to-an-existing-record)
 - [Replies to automatic notifications](../mail.html#replies-to-automatic-notifications)
 - [Replies to email threads](../mail.html#replies-to-email-threads)
 - [Based on Source and SourceID](../mail.html#based-on-source-and-sourceid)
 - [Based on ID in subject](../mail.html#based-on-id-in-subject)
- [Event matching](../mail.html#event-matching)

## Sending Email

Each Xurrent account has its own email address. The email address of a Xurrent account
is `example@mail.xurrent.com`, where `example` is the `id` of the account. You can
find the `id` of your organization’s Xurrent account when you open the ‘Account
Overview’ section in the Settings console.

In addition, each team that is registered in a Xurrent account can be given its own
email address. An email address of a team looks like
`team-name.example@mail.xurrent.com`, where `team-name` is the local part of the
email address that is unique for the account. This local part can be defined by
an administrator of the account.

When an email is sent to the email address of the account or one of its teams,
Xurrent uses the information of this email to generate a new request. If it was sent
to a team’s email address, the new request gets assigned to that team.

Another email address (e.g. one within your organization’s internet domain) can
be made available for each of these inbound email addresses. These email
addresses can then be used by end users and system management tools to send
their email to. Filters can then be applied in these mail accounts before they
forward email to their corresponding Xurrent email addresses.

It is important to verify that the Email Policy option ‘Allow inbound email to
generate new requests’ is checked. If it is not, an inbound email message will
not cause a new request to be generated and the sender of an email will receive
an email that is based on the email template ‘Email Rejected’.

Note, however, that it is not possible to send email to a directory account.
That is because requests cannot be stored in a directory account. When a
directory account is used, email needs to be addressed to one of its support
domain accounts, or a team that is registered in one of these support domain
accounts.

### Mail from end users

After an email has been received at the inbound email address of a Xurrent account
or one of its teams, the email is checked first to ensure that the sender is
allowed to register new requests in this Xurrent account. If a Person record exists
in this account, or in its directory account, with an email address that matches
the address of the sender, then the information of the email is used to generate
a new request.

Note that the Mail API first looks for a match with the primary email address of
a person. If a match cannot be found with a primary email address, then the Mail
API continues to look for a match by going through the other email addresses
that are specified in the Person records of the account, or its directory
account.

It is possible to configure Xurrent to automatically create a new Person record when
an email is received from an address that does not match an email address of any
of the existing Person records within the account, or its directory account.
This can be done in the Email Policy section of the [Settings
console](https://help.xurrent.com/help/settings_console).

The new request gets the following values:

- the Requested by and Requested for fields are set to the sender of the email,
- the Subject field is set to the subject of the email,
- a Note is added to the request with the contents of the email body,
- the Category field is set to `other`, and
- the Team field is set to the service desk team of the first line support
 agreement that covers the Xurrent account to which the email was sent, or if the
 email was sent to a team’s email address, the Team field is set to this team.

### Mail from monitoring tools

To allow a system management or monitoring tool to use the Mail API, a Person
record needs to be registered for it in Xurrent. This Person record needs to have an
email address (preferably the primary email address) that matches the `From`
email address of the email that the monitoring tool generates.

If the monitoring tool’s Person record has the Specialist role of a Xurrent
account, then it can include parameters in the email it sends to the email
address of this Xurrent account. Parameters are used to set field values in the new
request.

Parameters need to be specified at the start of an email’s body. An example of
an email with parameters is provided below:

nnm@example.com

example@mail.xurrent.com

Server CMP00001 Down

#source: Network Node Manager
#sourceID: 12345
#ci: CMP00001
#incident
#top

This text is added as a Note to the request.

Keep in mind that, in order for this example to work, a Person record with the
email address `nnm@example.com` needs to exist in a Xurrent account and this Person
record needs to have the Specialist role in the account which email address is
`example@mail.xurrent.com`. If this person does not have the Specialist role of this
account, the parameters are ignored.

### Overriding the From email address

When the Email Policy option ‘Allow email parameter #from’ is set, you can override
the From email address by adding the header fields `X-Xurrent-From` and `X-Xurrent-Auth`.
This allows the creation of a request on behalf of someone else.

For example this email will create a request on behalf of `beatrice.baldwin@example.com`:

```
From: demo-request-webform@example.com
X-Xurrent-From: beatrice.baldwin@example.com
X-Xurrent-Auth: SECRET
To: example@mail.xurrent.com,
Subject: Request for product demo

I would like to request a demo of your product.
```

To be accepted, the value for `X-Xurrent-Auth` must match a configured value in the
Email Policy and the email must pass the DMARC policy of the sending domain.

## Attachments

When an email contains one or more attachments, these files are automatically
attached below the note that the Mail API adds. The number of attachments that
can be added by the Mail API from an inbound email is limited to 20.

Inline images that are included in the body of the email get added as inline
images in the note that the Mail API adds.

## Default values

To simplify the creation of new requests by monitoring tools, default values are
used when parameters have not been provided for [request
fields](../../requests.html#fields) that are required.

category
: Set to `incident` if a service instance is to be related to the request. Otherwise, set to `other`.

created\_by
: Set to the sender of the email (Mail API does not allow any other value).

requested\_by
: Set to the sender of the email (Mail API does not allow any other value).

requested\_for
: Set to the sender of the email.

impact
: Set to `top` if category is `incident`. Otherwise the Impact field of the request is left empty.

member
: Set to the sender of the email if a valid member is not provided and a status is specified that causes the Member field of the request to be required. When the `template_id` parameter is used and the request template is linked to a workflow template, then the Member field of the request is set to the manager of the workflow.

service\_instance
: Set to the first service instance of the configuration item when a configuration item is specified for the request.

source
: Set to `Email`.

sourceID
: Set to the `Message-ID` value from the raw source of the email. (for example: `2142703314.3093062.1604928617247@mail.yahoo.com`).

status
: Set to `assigned`. When the `template_id` parameter is used and the request template is linked to a workflow template, then set to `workflow_pending`.

team
: The team to which the person specified as the `member` belongs. Otherwise, if a service instance is to be related to the request, the First Line Team of this service instance or, if a First Line Team is not specified or the sender of the email is a member of the First Line Team or the Support Team, the Support Team of this service instance. Else, set to the Service Desk Team of the first line support agreement that covers the account of the person selected in the Requested for field.
: Note: if an invalid team was specified in the email, the default team is selected in the request.

Relying on all default values makes it possible to create a request by providing only a subject in the email.

## Parameters

The following parameters are accepted to set the field values of a new request.
Parameters cannot be used to update the field values of an existing request.
Make sure you include a blank line between the parameters and the text of the email body.
Use the `#end` parameter to mark the end of the parameters section if a blank line cannot be placed between the parameters section and the start of the email body text.

category
: Used to specify an option in the Category field of the request. The available field options can be found in the [Fields](../../requests.html#fields) section of the Requests API page. Shortcuts are supported for this parameter. For example, `#category: rfc` is the same as `#rfc`.

ci
: Used to specify the configuration item that is to be related to the request. The configuration item needs to be identified by its label or, in case of a software CI, its Name field value.

ci\_id
: Used to specify the configuration item that is to be related to the request. The configuration item needs to be identified by its ID.

ci\_source
: Used together with the `ci_sourceID` parameter to specify the configuration item that is to be related to the request. This parameter should be used to specify the configuration item’s Source field value.

ci\_sourceID
: Used together with the optional `ci_source` parameter to specify the configuration item that is to be related to the request. The configuration item needs to be defined using its Source ID field value.

completion\_reason
: Used to specify an option in the Completion reason field of the request when its Status field is set to `completed`. The available field options can be found in the [Fields](../../requests.html#fields) section of the Requests API page. Shortcuts are supported for this parameter. For example, `#completion_reason: workaround` is the same as `#workaround`.

desired\_completion\_at
: Used to specify the date and time that has been agreed on for the completion of the request. The desired completion overwrites the automatically calculated resolution target of any affected SLA that is related to the request when the desired completion is later than the affected SLA’s resolution target. By default, the `requested_by` receives a notification based on the ‘Desired Completion Set for Request’ email template whenever the `desired_completion_at` is set, updated or removed.

downtime\_end\_at
: Used to specify the end date and time of a service outage. Be sure to use the correct [datetime format](../../general/data_types.html).

downtime\_start\_at
: Used to specify the start date and time of a service outage. Be sure to use the correct [datetime format](../../general/data_types.html).

end
: Used to indicate the end of the parameters section. Everything after this marker is considered to be part of the note text.

impact
: Used to specify an option in the Impact field of the request. The available field options can be found in the [Fields](../../requests.html#fields) section of the Requests API page. Shortcuts are supported for this parameter. For example, `#impact: high` is the same as `#high`.

internal
: Used to indicate that the contents of the email body is to be added to the request as an Internal Note.

markdown
: Used to indicate that the contents of the email body uses [Text Formatting](../../general/text_formatting.html).

member
: Used to specify the person to which the request is to be assigned. This person needs to be identified by the Person record’s Primary email field value.

member\_id
: Used to specify the person to which the request is to be assigned. This person needs to be identified by the Person record’s ID.

problem\_id
: Used to specify the problem that is to be related to the request. The problem needs to be identified by its ID.

requested\_for
: Used to specify the person who is to be selected in the Requested for field of the request. This person needs to be identified by the Person record’s Primary email field value. The `requested_for` parameter is processed only if the sender’s Person record has the Service Desk Analyst role.

requested\_for\_id
: Used to specify the person who is to be selected in the Requested for field of the request. This person needs to be identified by the Person record’s ID. The `requested_for_id` parameter is processed only if the sender’s Person record has the Service Desk Analyst role.

service\_instance
: Used to specify the service instance that is to be related to the request. The service instance needs to be identified by its Name field value.

service\_instance\_id
: Used to specify the service instance that is to be related to the request. The service instance needs to be identified by its ID.

source
: Used to specify the name of the monitoring tool, see [source](../../general/source.html). After the request has been created, this value is visible in its Audit Trail.

sourceID
: Used to specify the unique ID of the event for which the request is to be registered, see [source](../../general/source.html). After the request has been created, this value is visible in its Audit Trail.

status
: Used to specify an option in the Status field of the request. The available field options can be found in the [Fields](../../requests.html#fields) section of the Requests API page. Shortcuts are supported for this parameter. For example, `#status: completed` is the same as `#completed`.

supplier
: Used to specify the Organization to which the request has been submitted. The Organization needs to be identified by its Name field value.

supplier\_id
: Used to specify the Organization to which the request has been submitted. The Organization needs to be identified by its ID.

supplier\_requestID
: Used to specify the identifier under which the request has been registered at the supplier organization.

support\_domain
: Used to specify the support domain in which the request is to be registered. The support domain needs to be identified by its ID. The ID of a Xurrent account can be found in the ‘Account Overview’ section of the Settings console.

team
: Used to specify the team to which the request is to be assigned. The team needs to be identified by its Name field value.

team\_id
: Used to specify the team to which the request is to be assigned. The team needs to be identified by its ID.

template\_id
: Used to specify the request template that is to be applied to the request. This request template needs to be identified by its ID. It is important to note that the field values defined by the parameters in an email, including the text in the subject and body of the email, overwrite the values specified in the request template.

time\_spent
: Used to specify the time spent working on the request, in minutes.

waiting\_until
: Used to specify the date and time at which the status of the request is to be updated from `waiting_for` to `assigned`. Be sure to use the correct [datetime format](../../general/data_types.html).

workflow\_id
: Used to specify the workflow that is to be related to the request. The workflow needs to be identified by its ID.

### Custom fields

It is possible to assign values to custom fields that are defined in UI extensions. Each custom field and its value is defined on a line of its own. The parameter name is the ID of the custom field with `custom_field_` preprended. For example:

nnm@example.com

example@mail.xurrent.com

SAP P31

#requested\_for: phoebe.young@example.com @example
#template\_id: 12345
#custom\_field\_service\_team: SAP Basis Support
#custom\_field\_service\_owner: john.smith@example.com
#custom\_field\_cost\_center: CH999

### Text formatting

It is possible to include basic formatting in the text of the email body below the parameters. The available formatting options are described in the [Text Formatting](../../general/text_formatting.html) section. To make sure that the formatting is applied in the new note of the request, the `markdown` parameter needs to be included in the list of parameters at the top of the email body.

### Linking records of other accounts

If the Person record of the sender has the Specialist role of more than one Xurrent account, then it is important to make sure that the records that are to be linked to the new request are obtained from the correct account. In such cases it is important to uniquely identify each record specified in the parameters by adding the `id` of the record’s account.

This can be done as follows:

nnm@example.com

example@mail.xurrent.com

SAP P31

#requested\_for: jane.young@example.com @example
#ci: P31 @other\_account
#team: SAP Basis Support @other\_account
#member: john.smith@example.com @other\_account

In this example, the sender’s Person record must have the Service Desk Analyst
role of the `example` account, because the `requested_for` parameter is used to
submit the request on behalf of someone from the `example` account. In addition,
the sender’s Person record must have the Specialist role of the `other_account`
account to be able to link the configuration item, team and member records of
the `other_account` account to the new request.

## Adding a note to an existing record

When an email is received the content may be added as a note to an existing record.
This requires that the option ‘Allow replies to be added as notes’ is checked in the
Email Policy of the receiving Xurrent account, and the record to which a note is added
is allowed to be accessed by the sender, and the record:

- has not been in its final status for more than `<x>` days, or
- the last note that is visible to the email recipient has been created at most `<x>` days ago

The value of `<x>` can be configured by account administrators via the Provide feedback field
on the Self Service Settings form. It is set to 28 days by default.

If not all of these conditions are met, the Mail API opens a new request with
a note containing the body of the reply.

If all of the above conditions are met, the following matching options exist:

### Replies to automatic notifications

Xurrent sends out automatically generated email messages to notify people when
specific conditions have been met. When a recipient replies to such a
notification, the Mail API adds the reply as a Note to the request, problem,
release, workflow, task, project or project task for which the original email was
generated.

### Replies to email threads

If an email was send to multiple people where the inbound mailbox address was
mentioned in the To: or Cc: field of the email then a new request is created
in Xurrent. If someone replies to such an email then Xurrent will recognize this to be
part of an email thread, and will add the content as a note to the previously
created request.

For this to work email clients are expected to conform to the email standard
[RFC5322](https://datatracker.ietf.org/doc/html/rfc5322), and specifically
include correct `In-Reply-To` and `References` email headers.

### Based on Source and SourceID

It is also possible to update an existing request, problem, release, workflow,
workflow task, project or project task by sending a new email to the email address
of a Xurrent account (i.e. this email does not need to be a reply to an
automatically generated email message from Xurrent or part of a previous email thread). To do this,

- the `source` and `sourceID` of the existing request, problem, release, workflow, task, project or
 project task needs to be included as a parameter at the start of the body field of the email, and
- the option ‘Allow replies to be added as notes’ needs to be checked in the Email Policy.

The rules that are applied to each inbound email are:

- If `source` and `sourceID` matches an existing **request** that has not been completed for more than `<x>` days and the sender of the inbound email has write access to the request, or has an enabled person record in one of the request’s request accounts or their directory accounts, update this request by adding a note with the body and the attachments of the inbound email, else
- if `source` and `sourceID` matches an existing **problem** that has not been solved for more than `<x>` days and the sender of the inbound email has write access to the problem, update this problem by adding a note with the body and the attachments of the inbound email, else
- if `source` and `sourceID` matches an existing **release** that has not been completed for more than `<x>` days and the sender of the inbound email has write access to the release, update this release by adding a note with the body and the attachments of the inbound email, else
- if `source` and `sourceID` matches an existing **workflow** that has not been completed for more than `<x>` days and the sender of the inbound email has write access to the workflow, update this workflow by adding a note with the body and the attachments of the inbound email, else
- if `source` and `sourceID` matches an existing **workflow task** that has not been finished for more than `<x>` days and the sender of the inbound email has write access to the workflow task, or (in case of an approval task) has an enabled person record in one of the task’s task accounts or their directory accounts, update this workflow task by adding a note with the body and the attachments of the inbound email, else
- if `source` and `sourceID` matches an existing **project** that has not been completed for more than `<x>` days and the sender of the inbound email has write access to the project, update this project by adding a note with the body and the attachments of the inbound email, else
- if `source` and `sourceID` matches an existing **project task** that has not been finished for more than `<x>` days and the sender of the inbound email has write access to the project task, or has an enabled person record in one of the project task’s task accounts or their directory accounts, update this project task by adding a note with the body and the attachments of the inbound email.

If no match was made it tries to match based on an ID in the subject field next.

The value of `<x>` can be configured by account administrators via the Provide feedback field
on the Self Service Settings form.

### Based on ID in subject

It is also possible to update an existing request, problem, release, workflow,
workflow task, project or project task by sending a new email to the email address
of a Xurrent account (i.e. this email does not need to be a reply to an
automatically generated email message from Xurrent or part of a previous email thread). To do this,

- the ID of the existing request, problem, release, workflow, task, project or
 project task needs to be included in the Subject field of the email, and
- the option ‘Allow replies to be added as notes’ needs to be checked in the Email Policy.
- the option ‘Match on ID when found in the email subject’ needs to be checked in the Email Policy.

The rules that are applied to each inbound email are:

- Step 1 - Look up the first number in the Subject field of the inbound email. A
 match is made on a number in the subject field if the number has at least 6
 digits and is prefixed by nothing, a whitespace character, or the hash #
 character, and is postfixed by nothing, a whitespace character, or a
 word-break.
- Step 2 -
 - If the number matches an existing **request** that has not been completed for more than `<x>` days and the sender of the inbound email has write access to the request, or has an enabled person record in one of the request’s request accounts or their directory accounts, update this request by adding a note with the body and the attachments of the inbound email, else
 - if the number matches an existing **problem** that has not been solved for more than `<x>` days and the sender of the inbound email has write access to the problem, update this problem by adding a note with the body and the attachments of the inbound email, else
 - if the number matches an existing **release** that has not been completed for more than `<x>` days and the sender of the inbound email has write access to the release, update this release by adding a note with the body and the attachments of the inbound email, else
 - if the number matches an existing **workflow** that has not been completed for more than `<x>` days and the sender of the inbound email has write access to the workflow, update this workflow by adding a note with the body and the attachments of the inbound email, else
 - if the number matches an existing **workflow task** that has not been finished for more than `<x>` days and the sender of the inbound email has write access to the workflow task, or (in case of an approval task) has an enabled person record in one of the task’s task accounts or their directory accounts, update this workflow task by adding a note with the body and the attachments of the inbound email, else
 - if the number matches an existing **project** that has not been completed for more than `<x>` days and the sender of the inbound email has write access to the project, update this project by adding a note with the body and the attachments of the inbound email, else
 - if the number matches an existing **project task** that has not been finished for more than `<x>` days and the sender of the inbound email has write access to the project task, or has an enabled person record in one of the project task’s task accounts or their directory accounts, update this project task by adding a note with the body and the attachments of the inbound email, else
- Step 3 - Look up the next number in the Subject field of the inbound email
- Step 4 - Return to step 2 if a number was found, else
 use the information from the inbound email to register a new request

The value of `<x>` can be configured by account administrators via the Provide feedback field
on the Self Service Settings form.

## Event matching

If an email is received within 24 hours of the creation of an existing open
request that has the same `account`, `source`, `requested_for`,
`service_instance`, and `ci` parameters, then a new request does *not* get
generated. Instead, the body text (below the parameters) of the email is used to
add a new note to the existing request. To avoid duplicate notes, however, the
note is only added when it has attachments, or when its text is different from a previous note of the
existing request. If the note has no attachments and the body text is either blank or the same as a previous note,
then no changes are made to the existing request.

When the `service_instance` parameter is not included in the email, it is found
by looking up the service instance to which the configuration item is linked.
Once the service instance is known, the event matching starts.

When the `ci` parameter is not included in the email, event matching will
prevent the generation of a new request when the `subject` and `note`
parameters, as well as the `account`, `source`, and `requested_for` parameters
are the same as those of an existing open request that was generated within the
past 24 hours. In that case, no note will be added to the existing request, unless the email has attachments.
