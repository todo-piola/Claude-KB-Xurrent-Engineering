# Teams Import

Teams can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Teams import file can be found in [Teams API - Fields](../../teams.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Coordinator,Manager,Configuration Manager,Remarks,Work Hours,Time Zone,Members,Inbound Email Local Part,Agile Board
,,,0,"End-User Support, Chicago",tom.peterson@widget.com,chess.cole@widget.com,tom.peterson@widget.com,"Responsible for all workstations, monitors, and printers used by people of Widget's Manufacturing Center in Chicago.","Monday through Friday, 8:00am until 6:00pm",Central Time (US & Canada),"chess.cole@widget.com
tom.peterson@widget.com",,
,,,0,"SAP Development, North America",,chess.cole@widget.com,,"Responsible for the configuration and support of all SAP-based services for the Widget North America, Inc. organization.","Monday through Friday, 8:00am until 6:00pm",Eastern Time (US & Canada),,sap-development,
,,,0,"Database Administration",,chess.cole@widget.com,,,"Monday through Friday, 8:00am until 6:00pm",Eastern Time (US & Canada),,,
```

[download CSV](https://developer.xurrent.com/csv/teams.csv)
