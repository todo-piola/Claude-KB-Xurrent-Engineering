# Request Templates Import

Request Templates can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Request Templates import file can be found in [Request Templates API - Fields](../../request_templates.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Subject,Keywords,Registration Hints,Instructions,Note,Category,Impact,Service,End Users,Specialists,Configuration Item,Asset Selection,Workflow Template,Team,Member,Assign to Self,Supplier,Workflow Manager,Status,Completion Reason,UI Extension,Desired Completion,Mark as Urgent,Support Hours,Time Zone,Created At,Updated At,Copy Subject to Requests,Default Effort Class
,,,0,Compliment,"praise,commendation","Explain in the Note field the reason for wanting to compliment Widget's IT department. Whenever possible, include the IDs of any requests that are related, as well as the names of the people who were involved.
This request will be assigned to the IT manager. The IT manager will pass the compliment on to the people involved, as well as their managers.",,,compliment,,,1,1,,0,,"End-User Support, Chicago",chess.cole@widget.com,0,,,,,,,,,,2017-01-23T08:46:45-05:00,2017-11-17T10:30:31-06:00,0,
,,,0,Move desktop PC,,"Ensure that the desktop personal computer that needs to be moved is selected in the request.
In the Subject field, add the location from which the PC needs to be moved, as well as its destination (e.g. from room 101 to 202).

------
Note: Laptop computers, including their docking stations, may be moved by their users.","Ensure that all peripherals such as the monitor, keyboard, mouse and all cables are also moved.",,rfc,,Personal Computing,1,1,,1,8,,,0,,,workflow_pending,,,,,,,2017-04-14T10:31:18-05:00,2017-11-22T09:50:39-06:00,1,
,,,0,Provide external hard disk drive,,"Specify in the Subject field to whom the external hard disk drive is to be delivered.
Example:
Provide external hard disk drive to John Smith",,,rfc,,Personal Computing,1,1,,0,10,,,0,,tom.peterson@widget.com,workflow_pending,,,,,,,2017-10-19T07:52:23-05:00,2017-10-19T07:52:23-05:00,1,
```

[download CSV](https://developer.xurrent.com/csv/request_templates.csv)
