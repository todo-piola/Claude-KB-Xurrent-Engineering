# Holidays Import

Holidays can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Holidays import file can be found in [Holidays API - Fields](../../holidays.html#fields).

## CSV Example

```
ID,Source,Source ID,Name,Start At,End At,Calendars
,,,Thanksgiving 2013,2013-11-27T00:00,2013-11-28T24:00,"24x7 except Sunday 8:00pm until Monday 5:00am
Monday through Friday, 8:00am until 6:00pm"
,,,New Years Eve 2013,2013-12-31T15:00,2014-01-01T24:00,"24x7 except Sunday 8:00pm until Monday 5:00am
Monday through Friday, 8:00am until 6:00pm"
```

[download CSV](https://developer.xurrent.com/csv/holidays.csv)
