# Task Approvals Import

Task Approvals can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Task Approvals import file can be found in [Tasks API - Fields](../../tasks.html#fields).

## CSV Example

```
Task,Approver,Status,Planned Effort
21512,howard.tanner@widget.com,rejected,1
21531,brian.myers@widget.com,assigned,1
21531,frank.watson@widget.com,assigned,2
21531,grace.weller@widget.com,approved,1
21531,howard.tanner@widget.com,assigned,1
21531,tom.edwards@widget.com,approved,3
21531,tom.smith@widget.com,assigned,1
21531,tom.waters@widget.com,assigned,1
```

[download CSV](https://developer.xurrent.com/csv/task_approvals.csv)
