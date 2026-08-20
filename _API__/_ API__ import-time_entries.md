# Time Entries Import

Time Entries can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Time Entries import file can be found in [Time Entries API - Fields](../../time_entries.html#fields).

## CSV Example

```
ID,Source,Source ID,Person,Date,Started At,Time Spent,Time Allocation,Service,Customer,Request,Problem,Task,Project Task,Correction,Description,Effort Class ID,Effort Class,Deleted
,,,carla.cluster@widget.com,2018-09-10,,0:30,,,,48673 @wdc,,,,0,,1,Non-Billable Support - Business Hours,0
,,,ellen.brown@widget.com,2019-07-19,,5:00,,,,,,,19413 @wdc,0,,4,Billable Support - Business Hours,0
,,,ellen.brown@widget.com,2019-08-14,2019-08-14T14:29:59-05:00,4:00,Project - Digital Factory (DiFact) @wna-it,Manufacturing (SAP) @wna-it,"Widget North America, Manufacturing",,,,,0,Estimate cost of operations,4,Billable Support - Business Hours,0
```

[download CSV](https://developer.xurrent.com/csv/time_entries.csv)
