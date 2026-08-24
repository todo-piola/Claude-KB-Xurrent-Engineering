# Task Templates Import

Task Templates can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Task Templates import file can be found in [Task Templates API - Fields](../../task_templates.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Subject,Instructions,Note,Copy notes to workflow,Category,Impact,Team,Member,Required Approvals,Assign to Workflow Manager,Planned Effort Workflow Manager,Assign to Service Owner,Planned Effort Service Owner,Assign to Requester,Planned Effort Requester,Assign to Requester Manager,Planned Effort Requester Manager,Assign to Requester Business Unit Manager,Planned Effort Requester Business Unit Manager,Supplier,Planned Duration,Planned Effort,Mark as Urgent,Service Instances,Configuration Items,UI Extension,Created At,Updated At,PDF Design,Default Effort Class,Request Template,Request Service Instance
,,,0,Confirm availability of LAN connectivity,"Go to the new location to see if a wall outlet is available. If it is, find out whether it is patched by trying to establish a network connection using the wall outlet.

If a patched wall outlet is not available at the new location, set the status of this task to ""Failed"". This will notify the manager of the workflow, who will then add a task to ensure that a patched wall outlet is made available.",,1,risk_and_impact,,"End-User Support, Houston",,,,,0,,0,,0,,0,,,480,60,0,,,,2017-01-23T08:46:45-05:00,2017-11-17T10:30:31-06:00,,,,
,,,0,Move desktop PC to new location,"Pick up the desktop PC and its peripherals like its monitor and printer from the old location and move it to its new location (see request that is related to the workflow for details).

At the new location, connect the PC to the network and perform a quick test to ensure that the PC is properly connected to its peripherals and the network.",,0,implementation,medium,"End-User Support, Houston",,,,,0,,0,,0,,0,,,480,120,0,,,,2017-01-23T08:46:45-05:00,2017-11-17T10:30:31-06:00,,,,
,,,0,Specify new location in CI record of PC,Update the configuration management information by specifying the new location of the PC in its CI record.,,0,,implementation,none,"End-User Support, Houston",joseph.coleman@widget.com,,,,0,,0,,0,,0,,,240,60,0,,,,2017-01-23T08:46:45-05:00,2017-11-17T10:30:31-06:00,,,,
,,,0,Manager approval for external hard disk drive,"A request has been made for an external hard disk drive.
The one-time charge for an external hard disk drive is $250.00.
Support for the external hard disk drive is included in the service charges for the Personal Computing service.",,0,approval,,,,,1,60,0,,0,,0,,1,,,960,,0,,,,2017-01-23T08:46:45-05:00,2017-11-17T10:30:31-06:00,Default Workflow Summary,,,
,,,0,Provide external hard disk drive to user,Take an external hard disk drive a USB cable from stock and deliver then to the user.,,0,implementation,none,"End-User Support, Houston",,,,,0,,0,,0,,0,,,480,120,0,,,,2017-04-14T10:31:18-05:00,2017-11-22T09:50:39-06:00,,,,
,,,0,Order new external hard disk drive for storage and update CMDB,"1. Update the CI record of the external hard disk drive that was given out to a user by setting its status to ""In Production"" and linking it to the user.
2. Order a new external hard disk drive with a USB cable and register it in the CMDB with the status ""Ordered"".
3. Once the new external hard disk drive has been delivered, note down its serial number and place it, along with its USB cable, in the storage room.
4. Update the CI record of the external hard disk drive by adding its serial number, setting its status to ""In Stock"" and specifying that it is located in the ""Storage Room"".",,0,implementation,none,"End-User Support, Houston",joseph.coleman@widget.com,,,,0,,0,,0,,0,,,480,60,0,,,,2017-10-19T07:52:23-05:00,2017-10-19T07:52:23-05:00,,"Non-Billable Support - Business Hours",,
```

[download CSV](https://developer.xurrent.com/csv/task_templates.csv)
