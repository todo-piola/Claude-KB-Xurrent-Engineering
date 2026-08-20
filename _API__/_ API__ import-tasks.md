# Tasks Import

Tasks can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Tasks import file can be found in [Tasks API - Fields](../../tasks.html#fields).

## CSV Example

```
ID,Source,Source ID,Workflow,Template,Subject,Category,Impact,Team,Member,Required Approvals,Supplier,Supplier Request ID,Anticipated Assignment At,Assigned At,Planned Duration,Planned Effort,Start At,Completion Target At,Status,Finished At,Created At,Updated At,Instructions,Notes,Predecessors,Urgent,Custom Fields,Waiting Until,Service Instances,Configuration Items,PDF Design,Request Template,Request Service Instance,Request,Phase
,,,1,,Service owner approval and floor space assignment for new rack,approval,,,chess.cole@widget.com,1,,,,2014-02-02T17:08:00-06:00,720,,,,approved,2014-02-03T22:51:00-06:00,2014-10-11T19:49:30-05:00,2014-10-11T19:49:30-05:00,Assign the 2x2 floor tile area of the data center floor on which the new rack is to be installed.,"chess.cole@widget.com 2014-02-04T09:51:00-06:00
Place the new rack to the left of RCK00008.",,0,,,,Default Workflow Summary,,,,
,,,1,,"Order and install new 19"", 48U rack",implementation,none,"End-User Support, Chicago",tom.peterson@widget.com,,,,,2014-02-03T22:51:00-06:00,7200,720,,,completed,2014-02-14T18:38:00-06:00,2014-10-11T19:49:30-05:00,2014-10-11T19:49:30-05:00,"Submit purchase requisition using SAP. In the purchase requisition form, specify that a new NetShelter SX 19"" 48U Rack from the brand APC is needed.
Once the purchase order has been sent out by the purchasing department, specify the purchase order number and the expected delivery date in the Note field of this task.",,Service owner approval and floor space assignment for new rack,0,,,Data Center Rack Space,RCK00011,
,,,2,1,Confirm availability of LAN connectivity,risk_and_impact,,"End-User Support, Chicago",,,,,,2014-10-14T10:05:23-05:00,480,120,,2014-10-15T16:00:23-05:00,assigned,,2014-10-14T10:05:23-05:00,2014-10-14T10:05:23-05:00,"Go to the new location to see if a wall outlet is available. If it is, find out whether it is patched by trying to establish a network connection using the wall outlet.

If a patched wall outlet is not available at the new location, set the status of this task to ""Failed"". This will notify the manager of the workflow, who will then add a task to ensure that a patched wall outlet is made available.",,,0,,,,Default Workflow Summary,,,,
,,,2,2,Move desktop PC to new location,implementation,medium,"End-User Support, Chicago",,,,,2014-10-15T16:00:23-05:00,,480,120,,2014-10-16T15:00:23-05:00,registered,,2014-10-14T10:05:23-05:00,2014-10-14T10:05:23-05:00,"Pick up the desktop PC and its peripherals like its monitor and printer from the old location and move it to its new location (see request that is related to the workflow for details).

At the new location, connect the PC to the network and perform a quick test to ensure that the PC is properly connected to its peripherals and the network.",,Confirm availability of LAN connectivity,0,,,,,
,,,2,3,Specify new location in CI record of PC,implementation,none,"End-User Support, Chicago",tom.peterson@widget.com,,,,2014-10-16T15:00:23-05:00,,240,60,,2014-10-17T10:00:23-05:00,registered,,2014-10-14T10:05:23-05:00,2014-10-14T10:05:23-05:00,Update the configuration management information by specifying the new location of the PC in its CI record.,,Move desktop PC to new location,0,,,,Default Workflow Summary,,,,
,,,1,18,CAB approval,approval,,,,5,,,,2014-09-04T10:52:36Z,960,,,2014-09-05T20:00:36Z,in_progress,,2014-09-04T10:52:36Z,2014-09-04T10:54:00Z,Review the workflow summary to determine whether or not the workflow should be approved.,,"",0,,,,Default Workflow Summary,,,,
```

[download CSV](https://developer.xurrent.com/csv/tasks.csv)
