# Product Categories Import

Product Categories can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Product Categories import file can be found in [Product Categories API - Fields](../../product_categories/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Group,Reference,Rule Set,UI Extension
,,,0,Desktop PC or Workstation,Computer,computer/desktop_pc_or_workstation,physical_asset,
,,,0,Website,"",website,logical_asset_with_financial_data,
```

[download CSV](https://developer.xurrent.com/csv/product_categories.csv)

## Updating Existing Product Categories

Apart from specifying the `ID` or the `Source` and `Source ID` columns to find an existing record, Xurrent is also able to match existing records using the `Reference` value.

This means that when an `ID`, `Source` and `Source ID` are not provided in the import file, and the given `Reference` value matches one of the Product Categories in the current Account, all the fields of that product category will be overwritten with the values provided in this import file. If the `Source` and `Source ID` columns are present in the import file, these fields will be cleared in the product category that matches the given `Reference` value.
