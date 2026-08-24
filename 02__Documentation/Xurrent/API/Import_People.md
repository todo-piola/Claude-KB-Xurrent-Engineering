# People Import

People can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a People import file can be found in [People API - Fields](../../people.html#fields).

## CSV Example

```
ID,Primary Email,Source,Source ID,Disabled,Name,Picture URI,Organization,Job Title,Support ID,Authentication ID,Employee ID,Cost Per Hour,Manager,Site,Location,Information,Time Zone,Time Format 24h,Locale,Auto Translation,Do Not Translate Languages,Work Hours,VIP,UI Extension,Custom Data,Custom Fields,Created At,Updated At
,chess.cole@widget.com,,,0,Chess Cole,https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/people/original/6-430239.jpg,"Widget North America, Information Technology @widget",IT Manager,430239,,,200.0,ed.turner@widget.com @widget,Widget Manufacturing Center @widget,Room 305,"Experience & Interests:
- ISO 20000-1, ISO 20000-2 (ITIL)
- ISO 17799",Central Time (US & Canada),0,en-US,1,,,0,,,,2019-10-16T08:15:46-05:00,2019-10-16T08:22:55-05:00
,ed.turner@widget.com,,,0,Ed Turner,https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/people/original/6-430201.jpg,"Widget International, Corp. @widget",CIO,430201,,,500.0,gary.bowman@widget.com @widget,Widget International Headquarters @widget,Room 409,,Eastern Time (US & Canada),0,en-US,1,,,1,,,,2019-10-16T08:17:38-05:00,2019-10-16T08:22:53-05:00
,tom.peterson@widget.com,,,0,Tom Peterson,https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/people/original/6-430243.jpg,"Widget North America, Information Technology @widget",End-User Support Specialist,430243,,,100.0,chess.cole@widget.com @widget,Widget Manufacturing Center @widget,Room 309,"Experience & Interests:
- Windows 7, Vista, XP, Mac OS X
- Word, PowerPoint, Excel, Outlook, FrontPage
- Apple iPhone
- Microscan barcode readers",Central Time (US & Canada),0,en-US,1,,,0,,,,2019-10-16T08:19:37-05:00,2019-10-16T08:22:50-05:00
```

[download CSV](https://developer.xurrent.com/csv/people.csv)

## Updating Existing People

Apart from specifying the `ID` or the `Source` and `Source ID` columns to find an existing record, Xurrent is also able to match existing records using the `Primary Email` value.

This means that when an `ID`, `Source` and `Source ID` are not provided in the import file, and the given `Primary Email` address matches one of the People in the current Account, all the fields of that person will be overwritten with the values provided in this import file. If the `Source` and `Source ID` columns are present in the import file, these fields will be cleared in the person that matches the given `Primary Email` address.

## Directory Service Integration

Visit the [Directory Services](../directory_services/index.html) page for more information about how the Import API can be used to import employee information from Microsoft Active Directory or other [LDAP](http://en.wikipedia.org/wiki/Ldap) directory services.
