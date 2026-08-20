# Project Tasks Import

Project Tasks can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Project Tasks import file can be found in [Project Tasks API - Fields](../../project_tasks.html#fields).

## CSV Example

```
ID,Source,Source ID,Project,Template,Subject,Category,Phase,Supplier,Supplier Request ID,Planned Duration,Team,Planned Effort,Start At,Deadline,Anticipated Assignment At,Completion Target At,Assigned At,Finished At,Status,Required Approvals,Urgent,Instructions,Created At,Updated At,Notes,Predecessors,Custom Fields
,,,5450,Obtain estimates from suppliers for cost of purchases,Obtain estimates from suppliers for cost of purchases,activity,Initiation,,,1440,,,,,,,2016-09-28T13:53:00-05:00,2016-10-04T14:13:00-05:00,completed,,0,"Contact suppliers to get an idea of the equipment and services that will need to be obtained for the successful implementation of the project. Be sure to include recurring costs.",2016-12-23T05:09:07-06:00,2016-12-23T05:09:08-06:00,"","",
,,,5450,Estimate internal effort and cost,Estimate internal effort and cost,activity,Initiation,,,480,,,,,,,2016-10-04T14:13:00-05:00,2016-10-05T15:30:00-05:00,completed,,0,"Work with suppliers to estimate which skills the Widget organization will need to provide, and for how many workdays, to make the project a success. Provide an overview of when these internal workdays will need to be made available during the first 5 years following the start of the project. Determine the costs for this internal effort over these 5 years.",2016-12-23T05:09:07-06:00,2016-12-23T05:09:08-06:00,"",Obtain estimates from suppliers for cost of purchases,
,,,7497,Determine level of risk,Determine level of risk,activity,Initiation,,,960,,,,,,,2016-12-07T14:40:00-06:00,2016-12-09T16:01:00-06:00,completed,,0,"Describe the different risks that could cause this project to fail.",2016-12-23T05:09:09-06:00,2016-12-23T05:09:10-06:00,"",,
,,,7497,Find sponsor for project,Find sponsor for project,activity,Initiation,,,2400,,,,,,,2016-12-09T16:01:00-06:00,2016-12-10T13:47:00-06:00,completed,,0,"Determine which senior manager might be most interested in seeing this project get implemented.",2016-12-23T05:09:09-06:00,2016-12-23T05:09:10-06:00,",Determine level of risk,
,,,7497,Senior management approval for project,Senior management approval for project,approval,Initiation,,,720,,,,,,,2016-09-25T14:18:00-05:00,2016-09-27T15:22:00-05:00,in_progress,3,0,"Indicate whether this project should be implemented or not using the 'Approve' or 'Reject' options.",2016-12-23T05:09:06-06:00,2016-12-23T05:09:07-06:00,"",Find sponsor for project,
```

[download CSV](https://developer.xurrent.com/csv/project_tasks.csv)
