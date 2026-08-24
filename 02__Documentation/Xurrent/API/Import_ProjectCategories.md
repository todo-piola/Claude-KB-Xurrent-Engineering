# Project Categories Import

Project Categories can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Project Categories import file can be found in [Project Categories API - Fields](../../project_categories/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Name,Reference,Description,Information,Position
,,,0,Small,small,Less than 50 workdays and $50K,"A small project is not expected to exceed either of the following thresholds:

* Internal effort: 50 workdays
* Cost of purchases (including cost of external effort): $50K",1
,,,0,Medium,medium,Less than 200 workdays and $200K,"A medium project is expected to reach or exceed at least one of the following thresholds:

* Internal effort: 50 workdays
* Cost of purchases (including cost of external effort: $50K

But it is +not+ expected to exceed either of the following thresholds:

* Internal effort: 200 workdays
* Cost of purchases (including cost of external effort): $200K",2
,,,0,Large,large,More than 200 workdays or $200K,"A large project is expected to reach or exceed at least one of the following thresholds:

* Internal effort: 200 workdays
* Cost of purchases (including cost of external effort): $200K",3
```

[download CSV](https://developer.xurrent.com/csv/project_categories.csv)
