# Agile Board Columns Import

Agile Board Columns can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Agile Board Columns import file can be found in [Agile Boards - Columns API - Fields](../../agile_boards/columns.html#fields).

## CSV Example

```
"ID",Agile Board,Name,Position,WIP limit,Action Type,Dialog Type,Team,Member
1,Application Development,New,1,,none,none,,
2,Application Development,To Be Analyzed,2,,assign,full,Application Development,
3,Application Development,Analyze,3,3,start,none,,
4,Application Development,To Be Built,4,,assign,minimal,Application Development,
```

[download CSV](https://developer.xurrent.com/csv/agile_board_columns.csv)
