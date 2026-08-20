# Products Import

Products can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Products import file can be found in [Products API - Fields](../../products.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Brand,Model,Product ID,Category,Service,Support Team,Remarks,Supplier,Financial Owner,Depreciation Method,Useful Life,Rate,UI Extension,Active CIs,Custom Fields
,,,0,Dell Precision M4400 Laptop PC,Dell,Precision M4400,DL-M4400X1,computer/laptop_pc,Personal Computing,"End-User Support, Chicago","15.4 inch diagonal widescreen display with up to 1440x900 resolution.
2.26 GHz Intel Core 2 Duo P8400 processor.
128 GB (solid state), 160 GB, or 500 GB hard disk drive.
2 memory slots for up to 8 GB internal (RAM) memory.
Price indication: $1,500.","Best IT, Inc.","Widget North America, Inc.",straight_line,3,,,276,
,,,0,Microsoft Windows 7,Microsoft,,,software/operating_system_software,Personal Computing,"End-User Support, Chicago",License included In PC purchase price.,"Best IT, Inc.","Widget North America, Inc.",straight_line,3,,,2,
```

[download CSV](https://developer.xurrent.com/csv/products.csv)

## Discovery Tool Integrations

Visit the [Discovery Tools](../discovery_tools/index.html) page for more information about how the Import API can be used to import Product data that has been discovered by system management tools.
