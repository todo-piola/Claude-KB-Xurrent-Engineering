# People Contact Details Import

People Contact Details can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Contact details for People can include telephone numbers, email addresses, Skype and postal addresses.

To link contact details to a specific Person, the primary email address should be provided in the `Person` column.

Detailed information about the data that can be specified in the columns of a People Contact Details import file can be found in [Contacts API - Fields](../../contacts/index.html#fields) and [Addresses API - Fields](../../addresses/index.html#fields).

## CSV Example

```
Person,Contact Protocol,Contact Label,Contact URI,Address Label,Address Address,Address City,Address State,Address Zip,Address Country,Integration
chess.cole@widget.com,telephone,work,+1 (773) 288 2668,,,,,,,true
chess.cole@widget.com,telephone,fax,+1 (773) 288 2301,,,,,,,true
chess.cole@widget.com,website,personal,www.chesscole.net,,,,,,,true
chess.cole@widget.com,telephone,skype,chesscole1,,,,,,,true
chess.cole@widget.com,email,personal,chess.cole@gmail.com,,,,,,,true
chess.cole@widget.com,,,,home,505 North Michigan Avenue,Chicago,IL,60611,US,true
ed.turner@widget.com,telephone,work,+1 (212) 369 2604,,,,,,,true
ed.turner@widget.com,telephone,fax,+1 (212) 369 2601,,,,,,,true
tom.peterson@widget.com,telephone,work,+1 (773) 288 2672,,,,,,,true
tom.peterson@widget.com,telephone,fax,+1 (773) 288 2301,,,,,,,true
tom.peterson@widget.com,chat,chat_workchat,https://widget.facebook.com/chat/t/100215506159543,,,,,,,true
```

[download CSV](https://developer.xurrent.com/csv/people_contact_details.csv)

## Updating Existing Contact Details

If one or more rows of contact details are defined for a Person in the import file and the `Integration` value is set to `true` (or `1`), then all existing contact details of that Person, which `Integration` value is also `true`, will be removed during the import. Any contact details that were manually added for this Person (i.e. contact details which `Integration` value is `false`) will not be removed during imports.

Note that contact details which `Integration` value is `true` cannot be modified manually. It is possible, however, to use the Import API to change the `Integration` value of contact details from `true` to `false` or vice versa.

**Important**: Make sure all contact details for a Person are grouped together in the import file. Otherwise the last row of contact details in the import file will cause the previous contact details, which were added during the import for that same Person, to be removed.

If needed, it is also possible to specify the `ID` column to update existing contact details.

## Active Directory Integration

Visit the [Active Directory](../directory_services/index.html) page for more information about how the Import API can be used to import the contact details of people from Microsoft Active Directory or other [LDAP](http://en.wikipedia.org/wiki/Ldap) directory services.
