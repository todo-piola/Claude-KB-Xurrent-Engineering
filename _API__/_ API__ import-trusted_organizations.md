# Trusted Organizations Import

Trusted Organizations are provider organizations of active SLAs from trusted accounts, as well as the customer organizations of trusted accounts that are linked to an active SLA that is registered in your account.

Trusted Organizations can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Trusted Organizations import file can be found in [Organizations API - Fields](../../organizations.html#fields). Note that only the following fields can be specified:

`ID` `Name` `Remarks` `UI Extension` `Custom Fields` `Financial ID`

## CSV Example

```
ID,Name,Remarks,UI Extension,Custom Fields,Financial ID
,gigatera,"GigaTera, Inc.",,Organization,"[{""id"":""contact_person"",""value"":196}]",wdc-1234
,globalnet,"GlobalNet, Inc.",,Organization,"[{""id"":""contact_person"",""value"":219}]",wdc-5689
```

[download CSV](https://developer.xurrent.com/csv/trusted_organizations.csv)
