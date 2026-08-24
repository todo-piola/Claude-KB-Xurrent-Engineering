# Effort Classes Import

Effort Classes can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of an Effort Classes import file can be found in [Effort Classes API - Fields](../../effort_classes.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Cost Multiplier,Position,Created At,Updated At,Service Offerings
1,,,0,Non-Billable Support - Business Hours,1.0,1,2018-08-05T10:01:21-05:00,2018-08-05T10:01:21-05:00,"Bronze Mainframe
Bronze Microsoft Support"
2,,,0,Non-Billable Support - Overtime Mondays thru Saturdays,1.5,2,2018-08-05T10:01:21-05:00,2018-08-05T10:01:21-05:00,
3,,,0,Non-Billable Support - Overtime Sundays,2.0,3,2018-08-05T10:01:21-05:00,2018-08-05T10:01:21-05:00,
```

[download CSV](https://developer.xurrent.com/csv/effort_classes.csv)
