# Directory Services

The Import API is commonly used to establish an integration with Microsoft Active Directory or another [LDAP](http://en.wikipedia.org/wiki/Ldap) directory service. Most organizations already maintain their employee information in a directory service. It therefore makes sense for an organization to integrate its directory service with Xurrent to avoid having to maintain this information manually in two systems.

**Important** Some directory services also support [SCIM Provisioning](../../scim.html), which makes it possible to send user data to Xurrent without the need to roll your own integration.

## Integrating With Directory Services

Most organizations only have one directory service from which data need to be extracted for the maintenance of the Person records in Xurrent.

Even though information about organizations can be obtained from a directory service, it is normally easier to maintain the Organization records, and the hierarchical relations between them, manually in Xurrent. That is because the structure of an organization does not change very often. When organizations have tried to automate the maintenance of their organization structure using the data from a directory service, the result is often that too many organization records get generated because of inconsistencies in the way that organization names have been written in the directory service.

When a [People](../people.html) import file is prepared, however, it is still important to detect and address such inconsistencies in the naming of organization in the directory service. If the Organization that is specified in the [People](../people.html) import file does not exist in Xurrent, then the generation or update of this Person record will fail.

To import a Person record, only a few field values are required in the import file (see [People API - Fields](../../people.html#fields). The example below shows how the columns could be populated using data from a directory service.

```
Primary Email Source Name Organization	Job Title Site Location	Locale	Time Zone Time Format 24h
frank.williams@widget.com	Active Directory	Frank Williams	Widget USA	Sales Executive Chicago Sales Office	Room 202	en-US	Central Time (US & Canada)	0
pierre.lefevre@widget.com	Active Directory	Pierre Lefèvre	Widget France	Account Manager Paris Sales Office	Room 312	fr	Paris 1
```

Note that in the example above the `Primary Email` is used as the unique identifier for the people in the import file. This makes it possible for the directory service to update a Person record without knowing its `ID` ([see *Create or update*](../../import.html#create-or-update)).

After the People have been imported, the CSV or TSV file with the contact details of these people can be imported. Before starting the [People Contact Details](../people.html) import, however, use the [polling feature](../../import.html#import-progress) to make sure that the People import has completed and that it was successful.

The example below demonstrates how the Primary Email is used in the `Person` column of a [People Contact Details](../people.html) import file to ensure that People can be identified uniquely using data only from the directory service.

```
Person Contact Protocol	Contact Label	Contact URI Address Label	Address Address Address City	Address State	Address Zip	Address Country Integration
frank.williams@widget.com	telephone mobile +1 (713) 441 8299 1
pierre.lefevre@widget.com	telephone work +33 (1) 4703 5144 1
pierre.lefevre@widget.com home 14 Rue de Seine Paris 75006 FR 1
```

If one or more rows of contact details are defined for a Person in the import file and the `Integration` value is set to `true` (or `1`), then all existing contact details of that Person, which `Integration` value is also `true`, will be removed during the import. Any contact details that were manually added for this Person (i.e. contact details which `Integration` value is `false`) will not be removed during imports.

Note that contact details which `Integration` value is `true` cannot be modified manually. It is possible, however, to use the Import API to change the `Integration` value of contact details from `true` to `false` or vice versa.

**Important**: Make sure all contact details for a Person are grouped together in the import file. Otherwise the last row of contact details in the import file will cause the previous contact details, which were added during the import for that same Person, to be removed.

If needed, it is also possible to specify the `ID` column to update existing contact details.
