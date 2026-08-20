# Time Allocations Import

Time Allocations can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Time Allocations import file can be found in [Time Allocations API - Fields](../../time_allocations/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Group,Description Category,Service Category,Services,Customer Category,Customers,Default Effort Class
,,,0,Vacation,Time Off,hidden,none,"",none,"",
,,,0,Best in Customer Satisfaction (BICS),Project,required,selected,Service Management (Xurrent),selected,"Widget Europe, Information Technology @widget
Widget North America, Information Technology @widget",
,,,0,Administration,,hidden,none,"",any,"","Non-Billable Support - Business Hours"
```

[download CSV](https://developer.xurrent.com/csv/time_allocations.csv)
