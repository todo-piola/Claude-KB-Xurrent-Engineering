# Sprint Backlog Items Import

Sprint backlog items can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Sprint Backlog Items import file can be found in [Sprint Backlog Items API - Fields](../../sprints/backlog_items/index.html#fields).

## CSV Example

```
Sprint,Position,Request,Problem,Task,Project Task,Subject,Estimate,Planned,Done
565,1,69945,,,,Register a new expense via the app,3,1,1
565,2,69947,,,,Check my expenses of this month,2,1,1
565,3,69943,,,,Approval of expenses via the app,5,1,0
565,4,69951,,,,Add an approval delegate via the app,1,1,0
567,1,69959,,,,Broadcast via push notification on app,2,0,0
567,2,,219,,,Incorrect tab order from Expense Type field,,0,0
567,3,70457,,,,"No longer able to select the expense type ""Parking""",3,0,0
567,4,,221,,,Clicking on the Submit button does not submit new expense report,,0,0
568,4,70260,,,,Add ability to specify variance limits to the Quality Control application,,0,0
```

[download CSV](https://developer.xurrent.com/csv/sprint_backlog_items.csv)
