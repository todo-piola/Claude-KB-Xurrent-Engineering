# Product Backlog Items Import

Product Backlog Items can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Product backlog items can be removed adding a boolean `Remove` column to the import file. A CSV exported by Xurrent also contains a `Subject` column, such a column may be present in an import file but will be ignored by the import process.

The `Position` column can be left empty in an import file. In that case the importer will add a Request/Product that is not currently on the board at the bottom of the backlog.

## CSV Example

```
Product Backlog,Position,Request,Problem
My Backlog,1,60068,
My Backlog,2,80221,
My Backlog,3,80224,
My Backlog,4,,208
My Backlog,5,,220
My Backlog,6,60090,
My Backlog,7,70229,
My Backlog,8,70243,
My Backlog,9,80228,
My Backlog,10,80230,
My Backlog,11,80231,
My Backlog,12,80232,
My Backlog,13,50001,
```

[download CSV](https://developer.xurrent.com/csv/product_backlog_items.csv)
