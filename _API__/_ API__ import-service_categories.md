# Service Categories Import

Service Categories can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Service Categories import file can be found in [Service Categories API - Fields](../../service_categories/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Name,Description,Services
,,,Printing,"The Printing services provide the ability to print to local and network printers.","Network Printing;
Local Printing"
,,,Enterprise Applications,"These are the software application services that are used for the support of the business processes.","Customer Relationship Management (Siebel);
Expense Reporting;
Finance (SAP);
Sales Tracking"
```

[download CSV](https://developer.xurrent.com/csv/service_categories.csv)
