# Sprints Import

Sprints can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Sprints import file can be found in [Sprints API - Fields](../../sprints/index.html#fields).

## CSV Example

```
"ID",Source,Source ID,Scrum Workspace,Number,Status,Start At,End At,Description
565,,,Application Development,1,completed,2022-08-29T06:00:00-05:00,2022-09-12T04:00:00-05:00,Expense Reporting Release r12.4.1
566,,,Application Development,2,active,2022-09-12T04:15:00-05:00,2022-09-26T04:00:00-05:00,Expense Reporting Release r12.4.2
567,,,Application Development,3,registered,2022-09-26T04:15:00-05:00,,Expense Reporting Release r12.4.3
568,,,Heavy Iron,1,registered,,,
```

[download CSV](https://developer.xurrent.com/csv/sprints.csv)
