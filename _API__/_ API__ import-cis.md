# Configuration Items Import

Configuration Items can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Configuration Items import file can be found in [Configuration Items API - Fields](../../configuration_items/index.html#fields).

The `Has CI Relations` column can be used to incrementally synchronize Configuration Items in Xurrent to an external system, see [Configuration Item Relations Export](../ci_relations/index.html).

## CSV Example

```
ID,Source,Source ID,Product,Label,Name,System ID,Status,Site,Location,Support Team,Remarks,Nr of Processors,Nr of Cores,License Type,Nr of Licenses,Temporary License,License Expiry Date,Site License,Licensed Sites,Service,Service Instances,Users,Supplier,Serial Number,Financial Owner,PO Number,Asset ID,Depreciation Method,Purchase Value,In Use Since,Useful Life,Rate,Salvage Value,Warranty Expiry Date,Custom Fields,Has CI Relations,Created At,Updated At
,MS System Center,2066423,Dell Precision M4400 Laptop PC,CMP00021,Dell Precision M4400 Laptop PC,cmp00021.na.widget.com,in_production,,Mobile Device,"End-User Support, Chicago","15.4 inch diagonal widescreen display with up to 1440x900 resolution.
2.26 GHz Intel Core 2 Duo P8400 processor.
One 500 GB hard disk drive.
8 GB internal (RAM) memory.",,,,,0,,0,,Personal Computing,Personal Computing for IT Chicago,chess.cole@widget.com,"Best IT, Inc.",419Adi-0W2s03-016102,"Widget North America, Inc.",PO0044139,A00004846693,straight_line,1497.32,2009-03-28,3,,0.0,2010-03-27,,TRUE,2009-03-20T13:28:37-05:00,2017-08-13T06:31:17-05:00
,MS System Center,65231434,Microsoft Windows 7,LIC0000001,Microsoft Windows 7 Professional License Certificate,,in_production,Widget International Headquarters,"Room 316, Software Safe","End-User Support, Chicago","License included In PC purchase price.
Acquired with: CMP00001",,,installed_user_license,1,0,,0,,Personal Computing,,,"Best IT, Inc.",00043-511-724-929,"Widget North America, Inc.",,,na_cost_is_zero,,,,,,,,FALSE,2013-07-28T14:28:37-05:00,2017-06-14T10:01:21-05:00
,MS System Center,65422389,Microsoft Windows 7,,Microsoft Windows 7 Professional SP2,,archived,Widget International Headquarters,"Room 316, Software Safe","End-User Support, Chicago",License included In PC purchase price.,,,,,0,,0,,Personal Computing,,,,,,,,,,,,,,,,TRUE,2013-07-28T14:32:04-05:00,2017-06-17T11:43:19-05:00
,MS System Center,6503214,Microsoft Windows 7,,Microsoft Windows 7 Professional SP3,,in_production,Widget International Headquarters,"Room 316, Software Safe","End-User Support, Chicago",License included In PC purchase price.,,,,,0,,0,,Personal Computing,"Personal Computing for IT Chicago
Personal Computing for IT New York",,,,,,,,,,,,,,,FALSE,2013-10-15T11:52:11-05:00,2017-07-25T09:13:10-05:00
```

[download CSV](https://developer.xurrent.com/csv/cis.csv)

## Discovery Tool Integrations

Visit the [Discovery Tools](../discovery_tools/index.html) page for more information about how the Import API can be used to import Configuration Item data that has been discovered by system management tools.
