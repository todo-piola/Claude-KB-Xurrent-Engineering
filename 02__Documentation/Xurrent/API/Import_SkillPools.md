# Skill Pools Import

Skill Pools can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Skill Pools import file can be found in [Skill Pools API - Fields](../../skill_pools/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Picture URI,Cost Per Hour,Manager,Remarks,Members
,,,0,Software Architects,,100.0,howard.tanner@widget.com @widget,Members have at least 10 years of experience in application development,"grace.weller@widget.com @widget
tom.waters@widget.com @widget"
,,,0,SAP UEM Experts,,100.0,howard.tanner@widget.com @widget,"Members have a sound knowledge of SAP User Experience and know to define and provide metrics to monitor every application, business process, and transaction in SAP","deborah.burton@widget.com @widget
jan.molenaar@widget.com @widget
radoslaw.wisniewski@widget.com @widget"
```

[download CSV](https://developer.xurrent.com/csv/skill_pools.csv)
