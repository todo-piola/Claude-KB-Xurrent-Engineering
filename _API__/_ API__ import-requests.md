# Requests Import

Requests can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Requests import file can be found in [Requests API - Fields](../../requests.html#fields).

## CSV Example

```
ID,Source,Source ID,Permalink,Requested By,Requested For,Organization,Template,Knowledge Article,Grouped Into,Subject,Category,Impact,Service Instance,Configuration Item,Team,Member,Supplier,Supplier Request ID,Status,Problem,Change,Project,Completion Reason,Created By,Created At,Updated At,Resolution Target,Completed At,Downtime Start,Downtime End,Notes,Internal Notes,Reviewed,Urgent,Satisfaction,Addressed,Custom Fields,Waiting Until,Desired Completion,Agile Board,Agile Board Column,Agile Board Column Position
,,,,chess.cole@widget.com,chess.cole@widget.com,"Widget North America, Information Technology @widget",,,,"The ""Y"" key on keyboard no longer works",incident,medium,Personal Computing for IT Chicago,CMP00021,"End-User Support, Chicago",tom.peterson@widget.com,"Best IT, Inc.",1234,waiting_for,,,,,chess.cole@widget.com,2012-10-14T09:37:33-05:00,2012-10-14T09:38:01-05:00,2012-10-15T13:00:33Z,,,,"tom.peterson@widget.com 2012-10-14T09:38:01-05:00
Asked our PC supplier for assistance.","Note with sensitive information",0,1,,0,,,,Kanban Board,To Do,1
,,,,tom.peterson@widget.com,ed.turner@widget.com,"Widget Data Center, External IT @widget",,,,Add cost center for IT training,rfc,,Finance (SAP) Production,,"SAP Development, North America",,,,assigned,,,,,tom.peterson@widget.com,2012-10-14T09:39:31-05:00,2012-10-14T09:39:31-05:00,,,,,"","",0,0,,0,,,,,,
```

[download CSV](https://developer.xurrent.com/csv/requests.csv)

## Updating Existing Requests

When identifying an existing Request for an update using the `Source` and `SourceID` columns as described in the [Create or update?](../../import.html#create-or-update) section, the Request will be searched for in the account of the API user.
