# Organizations Time Allocations Import

Organizations Time Allocations can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

To link a time allocation to an organization, the name of the organization should be provided in the `Organization` column and the name of the time allocation should be provided in the `Time Allocation` column.

## CSV Example

```
Organization,Time Allocation
"Widget North America, Information Technology",Administration
"Widget North America, Information Technology",Travel
"Widget North America, Information Technology",Medical Leave
"Widget North America, Information Technology",Vacation
"Widget North America, Human Resources",Administration
"Widget North America, Human Resources",Travel
"Widget North America, Human Resources",Medical Leave
"Widget North America, Human Resources",Vacation
"Widget North America, Human Resources",Other
```

[download CSV](https://developer.xurrent.com/csv/organizations_time_allocations.csv)
