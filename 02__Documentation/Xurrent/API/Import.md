# Import API

The Import API makes it possible to create or update records in batches. The behavior of this API is similar to the [Import](https://help.xurrent.com/help/import) functionality as exposed via the GUI.

Importing records in batches through the API is the preferred way of building (one-way) integrations with [discovery tools](discovery_tools/index.html) and [directory services](directory_services/index.html). It allows for easily managed integrations and performs better compared to sending separate create/update REST API calls for each record.

This page is organized as follows:

- [Generating an import file](../import.html#generating-an-import-file)
- [Uploading an import file](../import.html#uploading-an-import-file)
- [Polling for the import progress](../import.html#import-progress)
- [Viewing the import log](../import.html#import-log)

## Generating an Import File

Data can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Each record in a CSV or TSV import file needs to be defined on a separate line. Each line of text is essentially a row of a spreadsheet. The first line of text is reserved for the column headers.

Each column header references a field of the record type. Not all column headers are required. If a column for a field is left out of an import file, it will cause the corresponding field to be set to its default value (usually this means that it is left empty) when the import causes new records to be generated. For existing records a missing column means that the corresponding field value will not be updated during the import.

Each [type](../import.html#type) of import file is described in a separate page within this section of the Xurrent Developer documentation. An example CSV file can be downloaded from each of these pages, so there is an example available for each type of import file.

Detailed information concerning the formatting of the values within the columns of an import file can be found in the [Data Types](../general/data_types.html#input) section. Use the [Enumerations API](../general/enumerations/index.html) to obtain a complete and up-to-date overview of all the values that can be selected in the fields that offer a fixed list of options (i.e. enumerations).

When in doubt, it is always possible to register a record with specific field values and relations to construct an example of what needs to be imported. Once that is done, an export can be performed. The export file will then contain the example with the values that need to be entered in the columns of an import file.

### Create or Update?

As stated above, each line in an import file represents one record in Xurrent. If the record already exists in Xurrent, it will get updated during the import. If the record does not yet exist, a new record will be created. The following steps are taken to determine whether a record already exists:

1. Each record in Xurrent is assigned a unique *ID*. If the `ID` column is present in the import file and a value is specified for a specific row, then Xurrent will try to find the existing record using this identifier.
2. If the `ID` column is not present or if its value is empty for a specific row, and the [`Source`](../general/source.html) and [`Source ID`](../general/source.html) columns are present and have a value, then these two values are used to find an existing record. If an existing record with this [`Source`](../general/source.html) / [`Source ID`](../general/source.html) combination is found, it will get updated. Alternatively, if such a record does not yet exist, then a new record will be generated. This new record will get the `Source` and `Source ID` values specified in the import file.

 As the [`Source`](../general/source.html) and [`Source ID`](../general/source.html) values are known by the external tool, this second step makes it easy for this external tool to fill out these values correctly. It eliminates the need for the external tool to know the IDs of the records it maintains in Xurrent.
3. For some [import types](../import.html#type) a special column is also accepted as a unique identifier:

 - `organizations_contact_details`: *Organization* - the organization’s name
 - `people`: *Primary Email* - the person’s email address
 - `people_contact_details`: *Person* - the person’s email address

 This step was introduced to enable updates of previously created Organization and Person records without first having to contact Xurrent to find their *ID*.

### Relating to Another Record

Xurrent records often have links to other Xurrent records. Each Person record, for example, can be related to a Site record. To indicate that a record has a link with another record, a unique value of the related record needs to be specified. This unique value is the Name field (which is unique within the account to which the record belongs) for the following records types:

- [Calendar](../calendars/index.html)
- [Holiday](../holidays.html)
- [Site](../sites.html)
- [Organization](../organizations.html)
- [Team](../teams.html)
- [Skill Pool](../skill_pools/index.html)
- [Service](../services.html)
- [Service Category](../service_categories/index.html)
- [Service Instance](../service_instances/index.html)
- [Service Offering](../service_offerings/index.html)
- [Service Level Agreement](../service_level_agreements.html)
- [SLA Notification Schemes](../sla_notification_schemes/index.html)
- [First Line Support Agreement](../first_line_support_agreements/index.html)
- [Product](../products.html)
- [Contract](../contracts/index.html)
- [PDF Design](../pdf_designs/index.html)
- [Project Task Template](../project_task_templates.html)
- [Project Task Template Assignment](../project_task_templates/assignments.html)
- [Project Template](../project_templates/index.html)
- [Scrum Workspace](../scrum_workspaces/index.html)
- [Waiting for Customer Follow-Up](../waiting_for_customer_follow_ups/index.html)

So, to indicate that a Person record is to be related to a specific Site, use the name of this Site to establish the link.

The name of a [Person](../people.html) record, however, should not be used to relate a record to a Person record. That is because the name of a Person record does not need to be unique within the account to which it belongs. The primary email address of the Person should therefore be used to establish links with Person records.

[Configuration items (CIs)](../configuration_items/index.html) are also special. Software versions have a unique name within the account to which they belong, so the name of software versions should be used to establish links. The name of software license certificates and other CIs do not need to be unique. Such CIs have a Label field, which value must be unique within the account. Hence, the label of such CI records can be used to link them to other records.

To relate a [product category](../product_categories/index.html) to a CI, the product category’s reference should be used. The reference of a product category is unique within the account.

To relate a [custom collection element](../custom_collection_elements/index.html) to a custom collection, the custom collection’s reference should be used. The reference of a custom collection is unique within the account.

The records of the types listed below have an ID that is unique within the account to which they belong. Use this ID to establish links with such records.

- [Request](../requests.html)
- [Request Template](../request_templates.html)
- [Problem](../problems.html)
- [Release](../releases.html)
- [Workflow](../workflows.html)
- [Task](../tasks.html)
- [Workflow Template](../workflow_templates.html)
- [Task Template](../task_templates.html)
- [Project](../projects/index.html)
- [Project Task](../project_tasks.html)
- [Project Task Assignment](../project_tasks/assignments.html)
- [Risk](../risks.html)

### Relating to Multiple Other Records

Some records can be related to multiple records of the same record type. For example, multiple Person records can be related as members to a Team record. To relate multiple Person records as members to a Team record, ensure that the primary email addresses of the members are separated by a line break. In addition, a double quote must be placed before the primary email address of the first member and a double quote must be placed after the primary email address of the last member of the Team.

Example:

```
"frank.watson@widget.com
grace.weller@widget.com
rodney.wilson@widget.com
thomas.wicker@widget.com
tom.waters@widget.com"
```

Note that if you are preparing an import file using a spreadsheet, then you only need to ensure that each reference to a record is placed on a separate line within the cell of the spreadsheet. The spreadsheet application should automatically ensure that the double quotes are correctly added when you save the file as a comma-separated values (CSV) file or tab-separated values (TSV) file.

### Relating to Different Accounts

When a trust relation has been established between two Xurrent accounts, it is possible for certain records of these accounts to be linked together. For example, Widget Data Center may be providing their Expense Reporting service to the Widget North America organization. After these organizations have established a trust relation between their accounts, Widget Data Center is able to register a Service Level Agreement and relate an Organization record of Widget North America to it as its customer. If the `id` of Widget North America’s account is “wna”, then Widget Data Center is able to define the link between the SLA record and the customer’s Organization record by placing the @ symbol between the customer’s record name and the `id` of the customer’s account.

This will then look as follows:

```
Widget North America @wna
```

## Uploading an Import File

The upload of a CSV or TSV file is done using the following API call:

```
$ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X POST \
 -F type=people -F file=@/tmp/people.csv \
 https://api.xurrent.com/v1/import
```

The response from the Import API is a token that acts as the unique identifier for the import job. This token can be used to retrieve [information about the progress](../import.html#import-progress) of the import job.

```
status: 200 OK
```

```
{"token":"68ef5ef0f64c012f2...e4598cdb41e68"}
```

It is important to note that the API user needs to have the Account Administrator role to be able to import files using the API. In the example above, the API user specifically needs to have the Account Administrator role of the account which `id` is “wdc”. The [Authentication section](../index.html#authentication) describes how the `api-token` of the API user can be found.

In the example above it would not be necessary to specify `-H "X-Xurrent-Account: wdc"` provided that the Person record of the API user is registered in the account which `id` is “wdc”.

### Parameters

The following parameters are supported:

file
: *Required* **file** — The [UTF-8](http://en.wikipedia.org/wiki/Utf-8) encoded [CSV](http://en.wikipedia.org/wiki/Comma-separated_values) or [TSV](http://en.wikipedia.org/wiki/Tab-separated_values) file to import as multi-part form-data.

type
: *Required* **[enum](../general/enumerations/index.html)** — The type of the file to import. Valid values, in a [specific order](../import.html#import-order), are:
: - [calendars](calendars/index.html)
 - [cis](cis/index.html)
 - [ci\_relations](ci_relations/index.html)
 - [closure\_codes](closure_codes/index.html)
 - [contracts](contracts/index.html)
 - [custom\_collections](custom_collections/index.html)
 - [custom\_collection\_elements](custom_collection_elements/index.html)
 - [custom\_views](custom_views.html)
 - [email\_templates](email_templates/index.html)
 - [first\_line\_support\_agreements](first_line_support_agreements/index.html)
 - [holidays](holidays.html)
 - [invoices](invoices.html)
 - [knowledge\_articles](knowledge_articles.html)
 - [notes](notes.html)
 - [organizations](organizations/index.html)
 - [organizations\_contact\_details](organizations_contact_details/index.html)
 - [organizations\_time\_allocations](organizations_time_allocations/index.html)
 - [out\_of\_office\_periods](out_of_office_periods/index.html)
 - [pdf\_designs](pdf_designs/index.html)
 - [people](people.html)
 - [people\_contact\_details](people_contact_details/index.html)
 - [people\_roles](people_roles.html)
 - [problems](problems.html)
 - [product\_categories](product_categories/index.html)
 - [products](products.html)
 - [projects](projects.html)
 - [project\_categories](project_categories/index.html)
 - [project\_tasks](project_tasks/index.html)
 - [project\_task\_assignments](project_task_assignments/index.html)
 - [project\_task\_templates](project_task_templates/index.html)
 - [project\_task\_template\_assignments](project_task_template_assignments/index.html)
 - [project\_templates](project_templates/index.html)
 - [releases](releases.html)
 - [requests](requests.html)
 - [request\_templates](request_templates.html)
 - [rfc\_types](rfc_types/index.html)
 - [risks](risks/index.html)
 - [risk\_severities](risk_severities/index.html)
 - [risk\_severities](risk_severities/index.html)
 - [scrum\_workspaces](scrum_workspaces/index.html)
 - [services](services/index.html)
 - [service\_categories](service_categories/index.html)
 - [service\_instances](service_instances/index.html)
 - [service\_offerings](service_offerings/index.html)
 - [service\_offering\_rfc\_type\_activity\_rates](service_offering_rfc_type_activity_rates/index.html)
 - [shop\_articles](shop_articles/index.html)
 - [shop\_article\_categories](shop_article_categories/index.html)
 - [shop\_order\_lines](shop_order_lines/index.html)
 - [short\_urls](short_urls/index.html)
 - [sites](sites/index.html)
 - [skill\_pools](skill_pools/index.html)
 - [slas](slas.html)
 - [sla\_coverage\_groups](sla_coverage_groups/index.html)
 - [sla\_notification\_schemes](sla_notification_schemes/index.html)
 - [sla\_notification\_rules](sla_notification_rules/index.html)
 - [slas\_financial\_details\_rfc\_type\_activities](slas_financial_details_rfc_type_activities/index.html)
 - [sprints](sprints/index.html)
 - [sprint\_backlog\_items](sprint_backlog_items/index.html)
 - [standard\_service\_requests](standard_service_requests/index.html)
 - [surveys](surveys/index.html)
 - [survey\_questions](survey_questions/index.html)
 - [survey\_responses](survey_responses/index.html)
 - [survey\_answers](survey_answers/index.html)
 - [tasks](tasks.html)
 - [task\_approvals](task_approvals/index.html)
 - [task\_templates](task_templates.html)
 - [task\_template\_approvals](task_template_approvals/index.html)
 - [teams](teams/index.html)
 - [timesheet\_settings](timesheet_settings.html)
 - [time\_allocations](time_allocations/index.html)
 - [time\_entries](time_entries.html)
 - [trusted\_organizations](trusted_organizations/index.html)
 - [ui\_extensions](ui_extensions/index.html)
 - [waiting\_for\_customer\_follow\_ups](waiting_for_customer_follow_ups/index.html)
 - [waiting\_for\_customer\_rules](waiting_for_customer_rules/index.html)
 - [workflow\_templates](workflow_templates.html)
 - [workflow\_types](workflow_types/index.html)
 - [workflows](workflows.html)

Click on any link above to view more detailed information on the format of the import file for the given type.

### Import order

It is not possible to establish a link with a record that does not yet exist in the Xurrent database. If you are using import files to populate a new Xurrent account, it is therefore important that the records are imported in a specific order. It is important, for example, that the Person records are loaded before an import of the Team records is performed. That allows each Team record to be linked to a coordinator, a manager, a configuration manager and several members during the import of the Team records.

## Import progress

The import process runs as a background job. Once the import job has been completed, the API user receives an email with a summary of the results.

In addition to these automated email notifications, it is also possible to check the progress of an import job automatically using the token received from the import response.

A common use case is to make sure that a [People import](people.html) has been completed before their [contact details](people_contact_details/index.html) are uploaded, or that the [Configuration Items](cis/index.html) are imported before their [relations](ci_relations/index.html) are uploaded. This is achieved by **polling** for the import progress every minute until `state` = `done` is returned.

Five minutes after the job is completed, the progress information is not available anymore through the API.

Example:

```
$ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X GET \
 https://api.xurrent.com/v1/import/68ef5ef0f64c012f2...e4598cdb41e68
```

Depending on the state of the import job, one of the following responses is returned:

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
{"state":"processing","line":990}
```

The job is being processed and the `line` attribute shows how much progress has been made.

### Done

```
status: 200 OK
```

```
{"state":"done","results":{"created":50,"updated":34,"deleted":0,"unchanged":7,"failures":0,"errors":0},"logfile":"https://itrp.amazonaws.com/imports/20170831/wdc/101550712561.sites.log?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJ...quest&X-Amz-Date=20170831T101630Z&X-Amz-Expires=172800&X-Amz-SignedHeaders=host&X-Amz-Signature=efffc5a...76f3b"}
```

The job is complete and the response includes meta information on the affected records.
If both the `failures` and `errors` attributes are zero, the entire upload was successful. If not, more detailed information on the failed records can be found in the [Import Log](../import.html#import-log). The URL of the import log is included at the end of the response.

Note that if the import process was able to recover from an error, the state `done` is returned. The response contains the state `error` as outlined below only when an error prevents the import job from continuing with the next row.

### Error

```
status: 200 OK
```

```
{"state":"error","message":"Invalid byte sequence in UTF-8 on line 15","results":{"created":5,"updated":2,"deleted":0,"unchanged":7,"failures":0,"errors":1},"logfile":"https://itrp.amazonaws.com/imports/20170831/wdc/101550712561.sites.log?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJ...quest&X-Amz-Date=20170831T101630Z&X-Amz-Expires=172800&X-Amz-SignedHeaders=host&X-Amz-Signature=efffc5a...76f3b"}
```

The import was aborted prematurely because of an unrecoverable error. A short description of the issue is provided in the `message` attribute. More detailed information can be found in the [Import Log](../import.html#import-log). The URL of the import log is included at the end of the response. Errors should always be investigated.

The `results` hash contains non-zero values in case the import file was partially processed.

### Not Found

```
status: 404 Not Found
```

The job was completed more than 5 minutes ago, so no progress information is available anymore. Information on the completed job can still be found in the [Import Log](../import.html#import-log).

## Import log

Each import job that is complete (with or without errors) is entered in the *System Logs* of the *Settings* console. Log into Xurrent as an Account Administrator and go to *Settings* => *System Logs* and select the *Import Log* view to see them all.

The `Level` column will contain `Fatal` in case an [error](../import.html#error) has occurred.
