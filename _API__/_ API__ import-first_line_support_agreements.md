# First Line Support Agreements Import

First Line Support Agreements can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a First Line Support Agreements import file can be found in [First Line Support Agreements API - Fields](../../first_line_support_agreements/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Status,Name,Customer,Customer Representative,Provider,Service Desk Team,Start Date,Notice Date,Expiry Date,Support Hours,Time Zone,Pickup Target,Pickups Within Target,First Call Resolutions,Service Desk Only Resolutions,Service Desk Resolutions,Rejected Solutions,Target Details,Charges,Remarks
,,,active,UpdatedFirst line support agreement for VirtualSupport,VS External,khunal.shrestra@virtualsupport.com,"VirtualSupport, Ltd.",Service Desk,2009-01-01,,,24x7 (Monday through Sunday),Mumbai,0:30,80,30,20,40,60,,UpdatedSupport is provided to internal customers. No charges apply.,
,,,active,First line support agreement for Widget North America,"Widget North America, Inc. @wna",chess.cole@widget.com @wna,"VirtualSupport, Ltd.",Service Desk,2009-01-01,2013-12-31,,24x7 (Monday through Sunday),Mumbai,1:30,40,60,30,40,40,,"Customer is charged $10 per request registered by VirtualSupport. In addition, customer is charged $10 per request completed by VirtualSupport.",
```

[download CSV](https://developer.xurrent.com/csv/first_line_support_agreements.csv)
