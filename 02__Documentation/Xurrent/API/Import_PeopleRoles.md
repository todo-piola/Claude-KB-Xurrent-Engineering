# People Roles Import

People Roles can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Roles can be related to a Person record to provide this Person certain access rights within the Xurrent service.

To link roles to a specific Person, the primary email address should be provided in the `Person` column.

Detailed information about the data that can be specified in the columns of a People Roles import file can be found in [People - Permissions API - Fields](../../people/permissions.html#fields).

## CSV Example

```
Person,Role Account,Specialist,Service Desk Analyst,Service Desk Manager,Problem Manager,Workflow Manager,Release Manager,Project Manager,Service Level Manager,Configuration Manager,Auditor,Account Administrator,Key Contact
chess.cole@widget.com,example,1,0,0,0,0,0,0,1,0,0,1,0
ed.turner@widget.com,example,0,0,0,0,0,0,0,0,0,1,0,0
tom.peterson@widget.com,example,1,0,0,1,1,0,0,0,1,0,0,0
```

[download CSV](https://developer.xurrent.com/csv/people_roles.csv)

## Updating Existing Roles

If one or more roles are defined for a Person in the import file, all roles for that Person specified during previous imports are overwritten.
