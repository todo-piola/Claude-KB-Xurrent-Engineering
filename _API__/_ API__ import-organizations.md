# Organizations Import

Organizations can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of an Organizations import file can be found in [Organizations API - Fields](../../organizations.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Business Unit,Business Unit Organization,Region,Parent Organization,Manager,Substitute,Remarks,UI Extension,Custom Fields,Financial ID
,,,0,"Widget North America, Inc.",1,"Widget North America, Inc.",NA,,,,"Widget North America, Inc. is a business unit of Widget International, Corp. It is responsible for all of Widget International, Corp.'s research & development, manufacturing and financial administration.",,,
,,,0,"Best IT, Inc.",0,,,,,,"Sales contact: Jeff Goodmann
Email: jeff.goodmann@best-it.com
Mobile: +1 (203) 876 4332",,,
,,,0,"Widget North America, Information Technology",0,"Widget North America, Inc.",NA,"Widget North America, Inc.",ed.turner@widget.com,chris.evans@widget.com,"The Information Technology department of Widget North America, Inc. is responsible for all information technology services within Widget North America, Inc.",,,
```

[download CSV](https://developer.xurrent.com/csv/organizations.csv)
