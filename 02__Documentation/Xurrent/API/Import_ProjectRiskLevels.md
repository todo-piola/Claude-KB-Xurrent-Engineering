# Project Risk Levels Import

Project Risk Levels can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Project Risk Levels import file can be found in [Project Risk Levels API - Fields](../../project_risk_levels/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Reference,Description,Information,Position
,,,0,Limited,limited,Risk of Failure is Limited,"A project is considered to have limited risk when:

1. The necessary internal resources are readily available for anticipated timeframe
2. The impact on customers, employees and suppliers is minimal
3. The success does not rely on technology that has not yet been proven within the Widget organization",1
,,,0,Moderate,moderate,Risk of Failure is Moderate,"A project is considered to have moderate risk when:

1. Backfilling will be required temporarily to free up internal project members
2. Many customers, employees and/or suppliers will notice some minor positive changes
3. The success relies on technology that is new to the Widget organization, but for which support is already readily available",2
,,,0,Significant,significant,Risk of Failure is Significant,"A project is considered to have significant risk when:

1. Number of FTEs will need to be increased or decreased to realize project's value
2. A large number of customers, employees and/or suppliers will experience significant changes
3. The success relies on unproven technology, or technology that is (or will soon be) unsupported",3
```

[download CSV](https://developer.xurrent.com/csv/project_risk_levels.csv)

## Updating Existing Project Risk Levels

Apart from specifying the `ID` or the `Source` and `Source ID` columns to find an existing record, Xurrent is also able to match existing records using the `Reference` value.

This means that when an `ID`, `Source` and `Source ID` are not provided in the import file, and the given `Reference` value matches one of the Project Risk Levels in the current Account, all the fields of that project risk level will be overwritten with the values provided in this import file. If the `Source` and `Source ID` columns are present in the import file, these fields will be cleared in the project risk level that matches the given `Reference` value.
