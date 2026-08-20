# Releases Import

Releases can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Releases import file can be found in [Releases API - Fields](../../releases.html#fields).

## CSV Example

```
ID,Source,Source ID,Subject,Manager,Impact,Completion Target At,Status,Completion Reason,Completed At,Created At,Updated At,Notes,Workflows
,,,Synchronize cost centers in Expense Reporting using data from SAP,frank.watson@widget.com,none,,completed,complete,2013-05-14T06:54:00Z,2013-02-23T23:33:00Z,2013-05-18T08:54:46Z,"frank.watson@widget.com 2013-02-23T23:33:00Z The objective of this release is to automate the synchronization of Widget North America's cost center data in Expense Reporting Production using data from SAP P31.","1499 1501"
,,,Automate exchange rate updates in Expense Reporting,frank.watson@widget.com,none,2013-05-31T20:00:00Z,implementation,,,2013-04-13T10:24:00Z,2013-05-25T15:42:20Z,"","1661 1663"
```

[download CSV](https://developer.xurrent.com/csv/releases.csv)
