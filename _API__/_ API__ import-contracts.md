# Contracts Import

Contracts can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Contracts import file can be found in [Contracts API - Fields](../../contracts/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Status,Name,Category,Customer,Customer Representative,Supplier,Supplier Contact,Start Date,Notice Date,Expiry Date,Time Zone,Remarks,Configuration items,UI Extension,Custom Fields
,,,active,BEST-07-0002677081 - Best IT Support & Maintenance for HP printers,support_and_maintenance_contract,Widget Data Center,joseph.coleman@widget.com,"Best IT, Inc.",,2013-09-11,,2015-09-10,Eastern Time (US & Canada),"Telephone support for hard- and software during business hours at +1 (800) 4-BEST-IT or +1 (800) 423 7848.
Next business day onsite repair.
Quarterly on-site cleaning and maintenance of each printer covered by the agreement.

Charges: $180 per printer per annum.","PRT00001
PRT00002
PRT00003
PRT00004
PRT00005",,
,,,active,22ZF34B - Dell 3-Year ProSupport for CMP00034,support_contract,Widget Data Center,joseph.coleman@widget.com,"Dell, Inc.",,2013-05-07,,2016-05-06,Central Time (US & Canada),"24x7 telephone support, 2 minutes or less average speed of answer.
Remote diagnosis: determination by online/phone technician of cause of issue.
Technician and/or part is dispatched, usually within 1 business day following completion of remote diagnosis.

Charges: Included in purchase price of configuration item.",CMP00034,,
,,,active,HPS07-0002431194 - HP Standard Continuous Support & Maintenance for HP-UX,support_and_maintenance_contract,Widget Data Center,carla.cluster@widget.com,Hewlett-Packard Company,,2008-12-14,,,Pacific Time (US & Canada),"Includes the following, if and when available:
- Support via web, email and telephone;
- Provides bug fixes, patches or workarounds for the most current releases and version of the software product in order to cause the software product to operate in substantial conformity with its then-current operating documentation;
- New releases or versions without additional charge.

Charges: 18% of license costs per annum.",HP-UX 11i v3,,
,,,active,LC00028154 - IT-Corporation Emergency Power Generators Lease Contract,lease_contract,Widget Data Center,carla.cluster@widget.com,"IT-Corporation, Inc.",,2007-11-16,,2013-11-15,Eastern Time (US & Canada),"The monthly lease charge is $1,658 per generator per month.","EPG01
EPG02",,
```

[download CSV](https://developer.xurrent.com/csv/contracts.csv)
