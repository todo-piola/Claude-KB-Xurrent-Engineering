# Sites Import

Sites can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Sites import file can be found in [Sites API - Fields](../../sites.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Address,City,State,Zip,Country,Time Zone,Remarks,UI Extension,Custom Fields
,,,0,Widget International Headquarters,1172 Park Avenue,New York,NY,10128,US,Eastern Time (US & Canada),,,
,,,0,Widget Manufacturing Center,5225 South Harper Avenue,Chicago,IL,60615,US,Central Time (US & Canada),This is where the widgets get made.,,
```

[download CSV](https://developer.xurrent.com/csv/sites.csv)
