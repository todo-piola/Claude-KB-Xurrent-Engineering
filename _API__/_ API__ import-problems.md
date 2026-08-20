# Problems Import

Problems can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Problems import file can be found in [Problems API - Fields](../../problems.html#fields).

## CSV Example

```
ID,Source,Source ID,Subject,Manager,Category,Impact,Service,Change,Project,Team,Member,Supplier,Supplier Request ID,Analysis Target At,Status,Known Error,Knowledge Article,Workaround,Solved At,Service Instances,Configuration items,Requests,Created At,Updated At,Notes,Urgent,Waiting Until
,,,Windows 7 shows Welcome screen for a long time,jennifer.granger@widget.com,reactive,high,Personal Computing,,,"End-User Support, Chicago",tom.peterson@widget.com,"Best IT, Inc.",121212,,waiting_for,1,,"Change the background from a solid color to a picture.
For users who want a solid background color, prepare a little (e.g. 10x10 pixel) png file of the desired color and set this file as the background.",,"Personal Computing for IT Boston
Personal Computing for IT Chicago
Personal Computing for IT New York","CMP00021
Microsoft Windows 7 Professional SP3",,,,"This is a known error, for which a workaround is already available.",0,
,,,SAP (P47) instance down,deborah.burton@widget.com,reactive,medium,Finance (SAP),,,"SAP Development, North America",chris.evans@widget.com,,,,progress_halted,0,,,,Finance (SAP) Production,,,,,"The T41 went down 2 days ago for an unknown reason.",1,
```

[download CSV](https://developer.xurrent.com/csv/problems.csv)
