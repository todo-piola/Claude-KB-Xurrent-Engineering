# App Offerings Import

App offerings can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a app offerings import file can be found in [App Offerings API - Fields](../../app_offerings/index.html#fields).

## CSV Example

```
"ID",Created At,Updated At,Source,Source ID,Disabled,Published,Latest,Name,Reference,Description,Features,Compliance,Service Instance,UI Extension Version,Webhook URI,Policy JWT Algorithm,Policy Audience,Policy Claim Expires In
1,2021-04-13T04:19:49-05:00,2021-04-13T04:19:51-05:00,,,0,0,1,Log Note Dispatcher Integration,note-dispatcher,Dispatch notes added to request to an external URL.,Fun translations,Kind of bad as all notes are logged,Translation Service EU,Note dispatcher configuration#1,https://dfgdgdfg.execute-api.eu-west-1.amazonaws.com/Prod/integration/?account={account},rs512,,
2,2021-04-13T04:20:25-05:00,2021-04-13T04:20:26-05:00,,,0,0,1,Typeform Integration,typeform,Very cool integration!,Everything and the kitchen sink,So compliant,Typeform Service,Typeform configuration#1,,rs256,,
```

[download CSV](https://developer.xurrent.com/csv/app_offerings.csv)
