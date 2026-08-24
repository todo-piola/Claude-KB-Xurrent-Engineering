# Project Import

Project can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Project import file can be found in [Project API - Fields](../../projects/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Subject,Manager,Program,Service,Customer,Category,Justification,Work Hours,Time Zone,Initial Risk Level,Initial Effort,Initial Value,Initial Cost of Effort,Initial Cost of Purchases,Status,Completion Target At,Completed At,Completion Reason,Created At,Updated At,Phases,Notes,Requests,Problems,Changes,UI Extension,Custom Fields
,,,Repainting of Houston conference rooms,ellen.brown@widget.com @widget,Data Center Improvements,Conference Room,Widget Data Center @widget,small,improvement,"Monday through Friday, 9:00am until 5:00pm",Central Time (US & Canada),limited,24,0.0,2400.0,0.0,completed,,2016-10-17T13:01:00-05:00,rejected,2016-09-27T10:51:00-05:00,2016-12-23T05:09:08-06:00,Initiation,"","","","",,
,,,Digital Operations Center (DOC),ellen.brown@widget.com @widget,Data Center Improvements,Service Management (Xurrent),Widget Data Center @widget,small,improvement,"Monday through Friday, 9:00am until 5:00pm",Central Time (US & Canada),limited,16,8000.0,1600.0,4000.0,in_progress,2016-12-20T16:34:00-06:00,,,2016-12-03T11:54:00-06:00,2017-01-12T14:48:02-06:00,"Initiation
Planning
Implementation","","","","",,
```

[download CSV](https://developer.xurrent.com/csv/projects.csv)
