# Workflows Import

Workflows can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Workflows import file can be found in [Workflows API - Fields](../../workflows.html#fields).

## CSV Example

```
ID,Source,Source ID,Template,Subject,Manager,Category,Impact,Service,Project,Release,Change Type,Justification,Start At,Completion Target At,Status,Completion Reason,Completed At,Created At,Updated At,Notes,Requests,Problems,Custom Fields,Phases
,,,,Install new rack for SAP servers,tom.peterson@widget.com,standard,none,Finance (SAP),,,infrastructure_change,expansion,2012-10-12T00:49:30Z,,completed,complete,2009-03-03T16:14:00-06:00,2009-02-02T17:08:00-06:00,2012-10-11T19:49:30-05:00,"tom.peterson@widget.com 2009-02-03T04:08:00-06:00
A new 19"", 48U rack is required to provide additional room for the new servers and disk arrays.",,,,
,,,,Move desktop personal computer,tom.peterson@widget.com,standard,medium,Personal Computing,,,infrastructure_change,move,2012-10-14T15:05:23Z,2012-10-17T10:00:23-05:00,risk_and_impact,,,2012-10-14T10:05:23-05:00,2012-10-14T10:05:23-05:00,"tom.peterson@widget.com 2012-10-14T10:05:23-05:00
If a wall outlet is not available at the new location, or if the wall outlet at the new location is not patched, an extra task should be added to this change to ensure a patched wall outlet is made available.",,,,
```

[download CSV](https://developer.xurrent.com/csv/workflows.csv)
