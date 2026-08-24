# Risks Import

Risks can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Risks import file can be found in [Risks API - Fields](../../risks.html#fields).

## CSV Example

```
ID,Source,Source ID,Subject,Manager,Severity,Status,Mitigation Target At,Closure Reason,Projects,Services,Organizations,UI Extension,Custom Fields
,,,Integration with cloud application could lead to breach of our Data Protection Policy,howard.tanner@widget.com @widget,High,closed,,transferred,"",Customer Relationship Management (Siebel),"Widget International, Corp. @widget",Risk,
```

[download CSV](https://developer.xurrent.com/csv/risks.csv)
