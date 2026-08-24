# Standard Service Requests Import

Standard Service Requests can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Standard Service Requests import file can be found in [Standard Service Requests API - Fields](../../standard_service_requests/index.html#fields).

## CSV Example

```
Service Offering,Request Template,Response Target,Resolution Target,Support Hours
Bronze Personal Computing,24,8:00,24:00,"Monday through Friday, 7:00am until 5:00pm"
Bronze Conference Room,5,4:00,40:00,"Monday through Friday, 7:00am until 3:00pm"
```

[download CSV](https://developer.xurrent.com/csv/standard_service_requests.csv)
