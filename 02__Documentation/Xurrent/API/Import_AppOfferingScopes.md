# App Offering Scopes Import

App offering scopes can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a app offering scopes import file can be found in [App Offering Scopes API - Fields](../../app_offerings/scopes/index.html#fields).

## CSV Example

```
"ID",Created At,Updated At,App Offering,App Offering ID,Effect,Actions
1,2021-04-13T04:20:25-05:00,2021-04-13T04:20:25-05:00,typeform,2,allow,"[""request:Read"",""request:Update""]"
```

[download CSV](https://developer.xurrent.com/csv/app_offering_scopes.csv)
