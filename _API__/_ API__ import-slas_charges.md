# Service Level Agreements - Rate IDs Import

Service Level Agreement Rate IDs can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

You need the Financial Manager role to use this import.

Detailed information about the data that can be specified in the columns of a Service Level Agreements Rate IDs import file can be found in [Service Level Agreements Effort Class Rate IDs API - Fields](../../service_level_agreements/effort_class_rateIDs/index.html#fields).

## CSV Example

```
Service Level Agreement,Effort Class,Rate ID
Bronze Conference Room for Widget Data Center (Houston),Billable Support,rate-id-123
Bronze Conference Room for Widget Data Center (Houston),Non-Billable Support,rate-id-456
"Bronze Local Printing for Widget Data Center, External IT",Billable Support,print-rate-123
"Bronze Local Printing for Widget Data Center, External IT",Non-Billable Support,print-rate-456
```

[download CSV](https://developer.xurrent.com/csv/slas_charges.csv)
