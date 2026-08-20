# Workflow Types Import

Workflow Types can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Workflow Types import file can be found in [Workflow Types API - Fields](../../workflow_types.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Reference,Description,Information,Position
,,,0,Application Change,application_change,,,1
```

[download CSV](https://developer.xurrent.com/csv/workflow_types.csv)

## Updating Existing Workflow Types

Apart from specifying the `ID` or the `Source` and `Source ID` columns to find an existing record, Xurrent is also able to match existing records using the `Reference` value.

This means that when an `ID`, `Source` and `Source ID` are not provided in the import file, and the given `Reference` value matches one of the Workflow Types in the current Account, all the fields of that workflow type will be overwritten with the values provided in this import file. If the `Source` and `Source ID` columns are present in the import file, these fields will be cleared in the workflow type that matches the given `Reference` value.
