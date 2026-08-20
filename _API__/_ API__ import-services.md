# Services Import

Services can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Services import file can be found in [Services API - Fields](../../services.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Keywords,Description,Provider,First Line Team,Support Team,Service Owner,Release Manager,Workflow Manager,Knowledge Manager,Problem Manager,Availability Manager,Capacity Manager,Continuity Manager
,,,0,Finance (SAP),,"The Finance service provides the ability to record all financial transactions for accounting, asset management, budgeting, and management reporting purposes. This is an SAP-based service that is specifically configured for the Widget North America, Inc. organization.","Widget North America, Information Technology",,"SAP Development, North America",deborah.burton@widget.com @widget,doug.kennedy@widget.com @widget,chris.evans@widget.com @widget,deborah.burton@widget.com @widget,deborah.burton@widget.com @widget,deborah.burton@widget.com @widget,deborah.burton@widget.com @widget,chris.evans@widget.com @widget
,,,0,Personal Computing,,"The Personal Computing service provides the functionality that the combination of a workstation (desktop or laptop) with its related hardware (e.g. monitor, keyboard, mouse, external drive, etc.) and operating system software makes available to its users. The service also provides the functionality that the workstation-based applications make available to its users. The Microsoft Internet Explorer browser application and Microsoft Outlook email client application are part of this service. The network interface cards of the workstations are also part of this service. The SAP client is not part of the Personal Computing service; it is part of the Finance (SAP) service.","Widget North America, Information Technology",,"End-User Support, Chicago",james.pitts@widget.com @widget,karri.otter@widget.com @widget,karri.otter@widget.com @widget,jennifer.granger@widget.com @widget,jennifer.granger@widget.com @widget,,,james.pitts@widget.com @widget
,,,0,Database,,The Database service provides a configured environment for applications to store and retrieve data.,"Widget North America, Information Technology",,Database Administration,chess.cole@widget.com,,,,,,,
```

[download CSV](https://developer.xurrent.com/csv/services.csv)
