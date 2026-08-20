# Calendars Import

Calendars can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Calendars import file can be found in [Calendars API - Fields](../../calendars/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Weekday,From,Until
,,,0,24x7 except Sunday 8:00pm until Monday 5:00am,mon,05:00,24:00
,,,0,24x7 except Sunday 8:00pm until Monday 5:00am,tue,00:00,24:00
,,,0,24x7 except Sunday 8:00pm until Monday 5:00am,wed,00:00,24:00
,,,0,24x7 except Sunday 8:00pm until Monday 5:00am,thu,00:00,24:00
,,,0,24x7 except Sunday 8:00pm until Monday 5:00am,fri,00:00,24:00
,,,0,24x7 except Sunday 8:00pm until Monday 5:00am,sat,00:00,24:00
,,,0,24x7 except Sunday 8:00pm until Monday 5:00am,sun,00:00,20:00
,,,0,"Monday through Friday, 8:00am until 6:00pm",mon,08:00,18:00
,,,0,"Monday through Friday, 8:00am until 6:00pm",tue,08:00,18:00
,,,0,"Monday through Friday, 8:00am until 6:00pm",wed,08:00,18:00
,,,0,"Monday through Friday, 8:00am until 6:00pm",thu,08:00,18:00
,,,0,"Monday through Friday, 8:00am until 6:00pm",fri,08:00,18:00
```

[download CSV](https://developer.xurrent.com/csv/calendars.csv)
