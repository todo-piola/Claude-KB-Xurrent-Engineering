# Out of Office Periods Import

Out of office periods can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Out of Office Periods import file can be found in [Out of Office Periods API - Fields](../../out_of_office_periods.html#fields).

## CSV Example

```
ID,Source,Source ID,Person,Time Allocation,Effort Class,Reason,Start At,End At,Approval Delegate,Created At,Updated At
,Xurrent,,howard.tanner@widget.com,General - Management @wdc,Non-Billable Support - Business Hours,CIO meeting,2019-11-19T06:00:00Z,2019-11-21T06:00:00Z,,2019-11-18T07:34:06-06:00,2019-11-18T10:55:59-06:00
,Xurrent,,ellen.brown@widget.com,Time Off - Vacation @wdc,,Time Off - Vacation,2019-11-18T06:00:00Z,2019-11-18T15:45:15Z,,2019-11-18T08:10:52-06:00,2019-11-18T09:45:16-06:00
```

[download CSV](https://developer.xurrent.com/csv/out_of_office_periods.csv)
