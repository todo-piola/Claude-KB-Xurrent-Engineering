# Organizations Contact Details Import

Organizations Contact Details can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Contact details for Organizations can include telephone numbers, email addresses and postal addresses.

To link contact details to a specific Organization, the name should be provided in the `Organization` column.

Detailed information about the data that can be specified in the columns of an Organizations Contact Details import file can be found in [Contacts API - Fields](../../contacts/index.html#fields) and [Addresses API - Fields](../../addresses/index.html#fields).

## CSV Example

```
ID,Organization,Contact Protocol,Contact Label,Contact URI,Address Label,Address Address,Address City,Address State,Address Zip,Address Country,Integration
,"Widget North America, Inc.",email,general,info@widget.com,,,,,,,true
,"Widget North America, Inc.",telephone,general,+1 (212) 369 2600,,,,,,,true
,"Widget North America, Inc.",website,general,www.widget.com,,,,,,,true
,"Widget North America, Inc.",telephone,fax,+1 (212) 369 2601,,,,,,,true
,"Widget North America, Inc.",,,,street,1172 Park Avenue,New York,NY,10128,US,true
,"Widget North America, Information Technology",telephone,general,+1 (212) 369 2630,,,,,,,true
,"Widget North America, Information Technology",telephone,fax,+1 (212) 369 2631,,,,,,,true
,"Widget North America, Information Technology",website,service_desk,https://widget.xurrent.com/,,,,,,,true
,"Widget North America, Information Technology",website,general,http://it.widget.com/,,,,,,,true
,"Widget North America, Information Technology",,,,street,5225 South Harper Avenue,Chicago,IL,60615,US,true
```

[download CSV](https://developer.xurrent.com/csv/organizations_contact_details.csv)

## Updating Existing Contact Details

If one or more rows of contact details are defined for an Organization in the import file and the `Integration` value is set to `true` (or `1`), then all existing contact details of that Organization, which `Integration` value is also `true`, will be removed during the import. Any contact details that were manually added for this Organization (i.e. contact details which `Integration` value is `false`) will not be removed during imports.

Note that contact details which `Integration` value is `true` cannot be modified manually. It is possible, however, to use the Import API to change the `Integration` value of contact details from `true` to `false` or vice versa.

**Important**: Make sure all contact details for one Organization are grouped together in the file. Otherwise the last contact details in the import file will overwrite the previous ones.

If needed, it is also possible to specify the `ID` column to update existing contacts. Using an `Integration` column with value `false` the integration flag can be removed and the contact becomes editable in the GUI.
