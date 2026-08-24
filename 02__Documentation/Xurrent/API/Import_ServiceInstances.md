# Service Instances Import

Service Instances can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Service Instances import file can be found in [Service Instances API - Fields](../../service_instances/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Status,Name,Service,First Line Team,Support Team,Remarks
,,,in_production,Finance (SAP) Production,Finance (SAP),,"SAP Development, North America",
,,,in_production,Personal Computing for IT Chicago,Personal Computing,,"End-User Support, Chicago",
,,,in_production,Database for SAP (P47),Database,,Database Administration,
```

[download CSV](https://developer.xurrent.com/csv/service_instances.csv)
