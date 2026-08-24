# SLA Notification Rules Import

SLA notification rules can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of an SLA notification rules import file can be found in [SLA Notification Rules API - Fields](../../sla_notification_schemes/sla_notification_rules/index.html#fields).

## CSV Example

```
"ID",SLA Notification Scheme,Threshold Percentage,Notify Current Assignee,Notify Service Owner,Notify Support Team Manager,Notify Support Team Coordinator,Notify First Line Team Manager,Notify First Line Team Coordinator
1,Scheme 1,25,1,0,0,0,0,0
2,Scheme 1,50,0,1,1,0,0,0
```

[download CSV](https://developer.xurrent.com/csv/sla_notification_rules.csv)
