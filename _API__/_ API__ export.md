# Export API

The Export API makes it possible to download update records from Xurrent in batches.
The behavior of this API is similar to the [Export](https://help.xurrent.com/help/import) functionality
as exposed via the GUI.

Exporting records in batches through the API is the preferred way of building
(one-way) integrations with, for example, a corporate data warehouse. It allows
for easily managed integrations and performs better compared to sending separate
GET REST API requests for each record.

This page is organized as follows:

- [Generating an export file](../export.html#generating-an-export-file)
- [Initiating an export](../export.html#initiating-an-export)
- [Polling for the export progress](../export.html#polling-for-the-export-progress)
- [Downloading an export file](../export.html#downloading-an-export-file)
- [Viewing the export log](../export.html#viewing-the-export-log)

## Generating an export file

Data can be exported from Xurrent in [UTF-8](http://en.wikipedia.org/wiki/Utf-8) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) files, or
as Microsoft Excel (.xlsx) files.

Each record in an export file is defined on a separate line.
The first line of text is reserved for the column headers.
Each column header references a field of the record type.

**Warning**: The names of the column headers do not change over time.
However, no guarantee is given about the order of the columns,
and new columns may be added by Xurrent at any time.
When processing an export file via automation, ensure to architect
your solution such that it can deal with changing positions of a column,
or the addition of new columns.

### Security Consideration

To avoid spreadsheet injection attacks, the following characters at the start
of an exported field value are prefixed by the tab character:
`=`, `+`, `-` or `@`.
This prevents the execution of commands when an export file is opened in a
spreadsheet application such as Microsoft Excel and Google Sheets.

### Relations to different accounts

When a trust relation has been established between two Xurrent accounts, it is
possible for certain records of these accounts to be linked together. For
example, Widget Data Center may be providing their Expense Reporting service to
the Widget North America organization. After these organizations have
established a trust relation between their accounts, Widget Data Center is able
to register a Service Level Agreement and relate an Organization record of
Widget North America to it as its customer. If the `id` of Widget North
America’s account is “wna”, then an export of Widget Data Center’s SLAs will
show the name of the customer’s Organization record followed by the @ symbol and
the `id` of the customer’s account.

This will then look as follows:

```
Widget North America @wna
```

## Initiating an export

The example below shows how an export of the Sites and Team records can be
extracted from an account which `id` is “wdc”, and how this export can be
limited to records that were created or updated after December 31, 2012.

```
$ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X POST \
 -F "type=sites,teams" -F "from=20121231" \
 -F "export_format=csv" -F "line_separator=lf" \
 "https://api.xurrent.com/v1/export"
```

The response from the Export API is a token that acts as the unique identifier
for the export job. This token can be used to retrieve [information about the
progress](../export.html#export-progress) of the export job.

```
status: 200 OK
```

```
{"token":"68ef5ef0f64c012f2...e4598cdb41e68"}
```

In case the `from` parameter is provided and there are no created or updated
records since that time no export will be scheduled. The following response will
be provided:

```
status: 204 No Content
```

It is important to note that the API user needs to have the [Account
Administrator role](../index.html#authentication) to be able to export files using the
API. In the example above, the API user specifically needs to have the Account
Administrator role of the account which `id` is “wdc”. The [Authentication
section](../index.html#authentication) describes how the
`api-token` of the API user can be found.

In the example above it would not be necessary to specify `-H "X-Xurrent-Account:
wdc"` provided that the Person record of the API user belongs to the account
which `id` is “wdc”.

### Parameters

The following parameters are supported:

type
: *Required* **[enum](../general/enumerations/index.html)** — The type of the file to export. Valid values are:
: - affected\_slas
 - agile\_board\_columns
 - agile\_boards
 - app\_offering\_automation\_rules
 - app\_offering\_scopes
 - app\_offerings
 - calendars
 - ci\_relations
 - cis
 - closure\_codes
 - contracts
 - custom\_collection\_elements
 - custom\_collections
 - custom\_views
 - effort\_classes
 - email\_templates
 - flsas
 - generic\_ci\_automation\_rules
 - generic\_project\_task\_automation\_rules
 - generic\_request\_automation\_rules
 - generic\_risk\_automation\_rules
 - generic\_task\_automation\_rules
 - generic\_workflow\_automation\_rules
 - holidays
 - invoices
 - knowledge\_articles
 - missing\_translations
 - notes
 - organizations
 - organizations\_contact\_details
 - organizations\_time\_allocations
 - out\_of\_office\_periods
 - outdated\_translations
 - pdf\_designs
 - people
 - people\_contact\_details
 - people\_roles
 - permission\_events
 - problems
 - product\_backlog\_items
 - product\_backlogs
 - product\_categories
 - products
 - project\_categories
 - project\_risk\_levels
 - project\_task\_assignments
 - project\_task\_template\_assignments
 - project\_task\_template\_automation\_rules
 - project\_task\_templates
 - project\_tasks
 - project\_template\_automation\_rules
 - project\_templates
 - projects
 - releases
 - request\_template\_automation\_rules
 - request\_templates
 - requests
 - risk\_severities
 - risks
 - satisfactions
 - scim\_group\_automation\_rules
 - scim\_user\_automation\_rules
 - scrum\_workspaces
 - service\_categories
 - service\_instances
 - service\_offering\_activity\_rates
 - service\_offering\_effort\_class\_rates
 - service\_offering\_ssr\_rates
 - service\_offerings
 - services
 - shop\_articles
 - shop\_order\_lines
 - short\_urls
 - sites
 - skill\_pools
 - sla\_coverage\_groups
 - sla\_financial\_details
 - sla\_financial\_details\_activities
 - sla\_financial\_details\_charges
 - sla\_notification\_rules
 - sla\_notification\_schemes
 - slas
 - sprint\_backlog\_items
 - sprints
 - standard\_service\_requests
 - survey\_answers
 - survey\_questions
 - survey\_responses
 - surveys
 - system\_logs
 - task\_approvals
 - task\_template\_approvals
 - task\_template\_automation\_rules
 - task\_templates
 - tasks
 - teams
 - time\_allocations
 - time\_entries
 - timesheet\_settings
 - translations
 - trusted\_organizations
 - ui\_extensions
 - workflow\_template\_automation\_rules
 - workflow\_templates
 - workflows
 - shop\_article\_categories

from
: *Optional* **[date](../general/data_types.html)** — The date after which a record needs to have been created or updated in order to be included in the export.

export\_format
: *Optional* **[enum](../general/enumerations/index.html)** — The format of the file to export. Valid values are:
: - csv
 - xlsx

line\_separator
: *Optional* **[enum](../general/enumerations/index.html)** — The format of the file to export. Valid values are:
: - lf
 - crlf

**Examples**

This defines the start of the day on May 24, 2013 in the timezone of the API
user: `from=20130524`

This also defines the start of the day on May 24, 2013 in the timezone of the
API user: `from=20130524T00:00:00`

This is equal to 11pm on May 01, 2013 in Sydney (i.e. in the AEST time zone):
`from=20130501T23:00:00-10:00`

This is the start of the day on May 01, 2013 in UTC (coordinated universal time):
`from=20130501T00:00:00Z`

The export format as csv and the line separator as carriage return and line feed
(CR and LF or 0x0D and 0x0A) control character:

- Export format: `export_format=csv`
- Line separator: `line_separator=crlf`

### Rate limit

Due to performance considerations, some limitations apply when exporting data.

For partial exports the `from` parameter has a maximum of 2 months backwards, with unlimited frequency.

Full exports can be performed multiple times per day unless the full export contains more than 10,000 records. In which case the full export for that record type can only be performed once per day.

## Polling for the export progress

The export process runs as a background job. The token received from the export
response can be used to retrieve information on the progress.

Five minutes after the job is completed, the progress information is not
available anymore through the API.

Example:

```
$ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X GET \
 https://api.xurrent.com/v1/export/68ef5ef0f64c012f2...e4598cdb41e68
```

Depending on the state of the export job, one of the following responses is
returned:

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
{"state":"processing","type":"sites","line":32}
```

The job is being processed and the `line` attribute shows how much progress has
been made.

### Done

```
status: 200 OK
```

```
{"state":"done","url":"https://...export.zip?AWSAccessKeyId...","expires_at":"2016-06-28T02:56:11-06:00"}
```

The job is complete and the response includes meta information about the export.
The `url` attribute will contain a link to the export file in case a single `type`
was exported. When multiple `type`s are exported at once, a ZIP file will be
created with a separate export file for each `type`. The `expires_at` attribute
shows when the `url` will expire. By default this is 2 days after the export job
completed.

**Warning**: When exporting to XLSX format, `type`s, for which more than 10.000
records are exported, are split into multiple files.

**Warning**: The name of the export file for each `type` contains the `type`
and has the appropriate extension (`.csv` or `.xlsx`), for example
`20211108-sites-123.csv` or `123-sites.csv`.
However, no other guarantee about the name of the export file is given.

### Failed

```
status: 200 OK
```

```
{"state":"failed","rate_limit_exceeded":"requests"}
```

The job has failed. Additional information is provided in the response body.
One common reason for failure is when the [Rate limit](../export.html#rate-limit) was exceeded.

More information on the failed job can still be found in the [Export Log](../export.html#viewing-the-export-log).

### Not Found

```
status: 404 Not Found
```

The job was completed more than 5 minutes ago, so no progress information is
available anymore. Information on the completed job can still be found in the
[Export Log](../export.html#viewing-the-export-log).

## Downloading an export file

It was already mentioned above that, when the Export API is used to start an
export, the immediate response from the Export API is a token that acts as the
unique identifier for the export job.

Once the export has been completed, an email is sent to the API user. This email
contains the hyperlink with which the export file can be downloaded. The header
of this email contains the token that is the unique reference to the export job.
This token makes it possible for automated scripts to find the correct email.

For example:

```
X-Mailer: Xurrent Mailer
X-Xurrent-Export: 68ef5ef0f64c012f2...e4598cdb41e68
X-Xurrent-ExportID: 12345
Auto-Submitted: auto-generated
```

## Viewing the export log

Each export job that is complete is entered in the *System Logs* of the
*Settings* console. Log into Xurrent as an Account Administrator and go to
*Settings* => *System Logs* and select the *Export Log* view to see them all.
