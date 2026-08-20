# Invoices Import

Invoices can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Invoices import file can be found in [Invoices API - Fields](../../invoices.html#fields).

## CSV Example

```
ID,Source,Source ID,Description,Project,Service,Supplier,PO Number,Invoice Number,Invoice Date,Remarks,Unit Price,Quantity,Amount,Capital Expenditure,Created At,Updated At
,,,HP ProLiant BL260c servers,7497,Digital Operations Center (DOC),HP,PO33729-01,36798292-A,2017-11-19,These are the 2 servers for the DOC project.,3600,2,,1,,
,,,APC NetShelter rack,7497,Digital Operations Center (DOC),"Connect IT Infrastructure, Inc.",PO663780,170092403,2017-11-03,Rack for the 2 new HP servers.,1408,1,,1,,
```

[download CSV](https://developer.xurrent.com/csv/invoices.csv)
