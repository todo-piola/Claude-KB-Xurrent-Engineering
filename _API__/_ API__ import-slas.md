# Service Level Agreements Import

Service Level Agreements can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Service Level Agreements import file can be found in [Service Level Agreements API - Fields](../../service_level_agreements.html#fields).

## CSV Example

```
ID,Source,Source ID,Status,Name,Service Offering,Service Instance,Service Level Manager,Customer,Customer Representatives,Start Date,Notice Date,Expiry Date,Remarks,Use Knowledge From Service Provider,Coverage,Organizations,Sites,People,Service Instances
,,,active,"Silver Personal Computing for Widget North America, Information Technology",Silver (Chicago only) Personal Computing,Personal Computing for IT Chicago,chess.cole@widget.com,"Widget North America, Information Technology",ed.turner@widget.com,2012-10-20,,,,0,cis_of_service_instance,,,,
,,,active,"Standard Finance for Widget North America",Standard Finance (SAP),Finance (SAP) Production,chess.cole@widget.com,"Widget North America, Information Technology",ed.turner@widget.com,2012-10-20,,,,0,organizations,"Widget North America, Inc.",,,
,,,active,Premium Oracle Database for the SAP P47,Premium Oracle Database,Database for SAP (P47),chess.cole@widget.com,"Widget North America, Information Technology",ed.turner@widget.com,2012-10-20,,,,1,service_instances,,,,Finance (SAP) Production / down
```

[download CSV](https://developer.xurrent.com/csv/slas.csv)

## Updating Existing SLAs

When identifying an existing SLA for an update using the `Source` and `SourceID` columns as described in the [Create or update?](../../import.html#create-or-update) section, the SLA will be searched for in the account of the API user.

## Relating Multiple Service Instances

For each service instance that is specified in the `Service Instances` column, Xurrent needs to know whether the service instance will either be ‘down’ or only ‘degraded’ when the service instance that is specified in the `Service Instance` column is down.

Therefore an extension is used to the [standard way of relating to multiple other records](../../import.html#relating-to-multiple-other-records):

```
"Expense Reporting Production / down
SAP Production / degraded"
```
