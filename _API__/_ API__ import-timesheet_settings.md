# Timesheet Settings Import

Timesheet Settings can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Timesheet Settings import file can be found in [Timesheet Settings API - Fields](../../timesheet_settings/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Assignment Time Tracking,Allocation Time Tracking,Require Note,Workday,Workweek,Allow Workday Overtime,Allow Workweek Overtime,Unit,Increment,Organizations,Effort Classes,Default Effort Class for Requests,Default Effort Class for Change Tasks,Default Effort Class for Project Tasks,Default Effort Class for Problems,Default Effort Class for Time Allocations
,,,0,"8hr workday, 40hr workweek, hours&minutes, 1hr incr.",true,true,false,480,2400,true,true,hours_and_minutes,60,"Widget Data Center, External IT
Widget Data Center, Internal IT
Widget North America, Finance
Widget North America, Human Resources
Widget North America, Information Technology","Non-Billable Support - Business Hours
Billable Support - Business Hours",,"Non-Billable Support - Business Hours",,,,
,,,0,"7:30 workday, 36hr workweek, percentage, min. 12.5%",true,true,false,450,2160,false,false,percentage_of_workday,12.5,"Widget Europe, Human Resources",,,,,,
```

[download CSV](https://developer.xurrent.com/csv/timesheet_settings.csv)
