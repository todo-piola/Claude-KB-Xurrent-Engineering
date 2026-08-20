# Risk Severities Import

Risk Severities can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Risk Severities import file can be found in [Risk Severities API - Fields](../../risk_severities/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Reference,Description,Information,Position
,,,0,Low,low,Risk is Low,"A risk is considered to be low when:

1. Likelihood is Low and Impact is Low
2. Likelihood is Low and Impact is Medium
3. Likelihood is Medium and Impact is Low",1
```

[download CSV](https://developer.xurrent.com/csv/risk_severities.csv)

## Updating Existing Risk Severities

Apart from specifying the `ID` or the `Source` and `Source ID` columns to find an existing record, Xurrent is also able to match existing records using the `Reference` value.

This means that when an `ID`, `Source` and `Source ID` are not provided in the import file, and the given `Reference` value matches one of the Risk Serverities in the current Account, all the fields of that risk severity will be overwritten with the values provided in this import file. If the `Source` and `Source ID` columns are present in the import file, these fields will be cleared in the risk severity that matches the given `Reference` value.
