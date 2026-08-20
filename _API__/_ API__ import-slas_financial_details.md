# Service Level Agreements - Financial Details Import

Service Level Agreement Financial Details can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

You need the Financial Manager role to use this import.

Detailed information about the data that can be specified in the columns of a Service Level Agreements Financial Details import file can be found in [Service Level Agreements API - Fields](../../service_level_agreements.html#fields).

## CSV Example

```
Service Level Agreement,Agreement ID,Activity ID top,Activity ID high,Activity ID medium,Activity ID low,Activity ID RFC,Activity ID RFI
Bronze Conference Room for Widget Data Center (Houston),agreement-id-123,activity-top-123,activity-high-123,activity-medium-123,activity-low-123,activity-rfc-123,activity-rfi-123
"Bronze Local Printing for Widget Data Center, External IT",agreement-id-456,activity-top-456,activity-high-456,activity-medium-456,activity-low-456,activity-rfc-456,activity-rfi-456
```

[download CSV](https://developer.xurrent.com/csv/slas_financial_details.csv)
