# Closure Codes Import

Closure Codes can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Closure Codes import file can be found in [Closure Codes API - Fields](../../closure_codes/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Reference,Description,Information,Position
,,,0,Hardware Issue - Resolved,hardware_issue_resolved,Hardware issue resolved successfully,"This closure code is used when a hardware-related request has been successfully resolved and the issue has been fixed. The request can be closed with this code when:

1. The reported hardware issue has been identified and addressed
2. The hardware solution has been implemented and tested
3. The requester has confirmed the hardware resolution is satisfactory",1
,,,0,Hardware Issue - Canceled,hardware_issue_canceled,Hardware issue request was canceled,"This closure code is used when a hardware-related request has been canceled before completion. The request can be closed with this code when:

1. The requester has withdrawn the hardware request
2. The hardware request is no longer needed
3. The hardware request has been superseded by another request",2
,,,0,Software Issue - Duplicate,software_issue_duplicate,Duplicate software issue request,"This closure code is used when a software-related request is identified as a duplicate of an existing request. The request can be closed with this code when:

1. The software issue has already been reported in another request
2. The duplicate request provides no additional information
3. The original request is being processed or has been resolved",3
```

[download CSV](https://developer.xurrent.com/csv/closure_codes.csv)

## Updating Existing Closure Codes

Apart from specifying the `ID` or the `Source` and `Source ID` columns to find an existing record, Xurrent is also able to match existing records using the `Reference` value.

This means that when an `ID`, `Source` and `Source ID` are not provided in the import file, and the given `Reference` value matches one of the Closure Codes in the current Account, all the fields of that closure code will be overwritten with the values provided in this import file. If the `Source` and `Source ID` columns are present in the import file, these fields will be cleared in the closure code that matches the given `Reference` value.
