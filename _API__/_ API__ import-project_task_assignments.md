# Project Task Assignments Import

Project Task Assignments can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Project Task Assignments import file can be found in [Project Task Assignments API - Fields](../../project_task_templates/assignments.html#fields).

## CSV Example

```
Project Task,Assignee,Status,Waiting Until,Planned Effort
19802,ellen.brown@widget.com @widget,completed,,2
19803,ellen.brown@widget.com @widget,waiting_for,2017-02-20T15:00:00Z,16
24021,ellen.brown@widget.com @widget,completed,,24
24022,ellen.brown@widget.com @widget,completed,,8
24023,howard.tanner@widget.com @widget,approved,,1
24023,ed.turner@widget.com @widget,approved,,1
24023,hank.williams@widget.com @widget,assigned,,4
```

[download CSV](https://developer.xurrent.com/csv/project_task_assignments.csv)
