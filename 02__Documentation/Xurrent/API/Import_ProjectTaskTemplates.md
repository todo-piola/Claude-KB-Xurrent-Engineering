# Project Task Templates Import

Project Task Templates can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Project Task Templates import file can be found in [Project Task Templates API - Fields](../../project_task_templates.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Subject,Instructions,Note,Copy notes to project,Category,Required Approvals,Assign to Project Manager,Planned Effort Project Manager,Assign to Service Owner,Planned Effort Service Owner,Assign to Requester,Planned Effort Requester,Assign to Requester Manager,Planned Effort Requester Manager,Assign to Requester Business Unit Manager,Planned Effort Requester Business Unit Manager,Supplier,Planned Duration,Team,Planned Effort,Created At,Updated At,PDF Design,Default Effort Class
,,,0,Obtain estimates from suppliers for cost of purchases,Contact suppliers to get an idea of the equipment and services that will need to be obtained for the successful implementation of the project. Be sure to include recurring costs.,,0,activity,,1,16,0,,0,,0,,0,,,1440,,,2017-01-23T08:46:45-05:00,2017-11-17T10:30:31-06:00,,
,,,0,Approval from steering committee for pilot implementation,"Present the plans for the pilot to the steering committee.
The scope of the pilot (in terms of geography, participants and duration), as well as the minimum levels of success that will need to be achieved during the pilot, need to be reviewed and approved by the steering committee.",,0,approval,3,0,,1,1,0,,1,1,1,1,,720,,,2017-04-14T10:31:18-05:00,2017-11-22T09:50:39-06:00,Default Project Summary,"Non-Billable Support - Business Hours"
,,,0,Go-live,,,0,milestone,,0,,0,,0,,0,,0,,,0,,,2017-10-19T07:52:23-05:00,2017-10-19T07:52:23-05:00,,
```

[download CSV](https://developer.xurrent.com/csv/project_task_templates.csv)
