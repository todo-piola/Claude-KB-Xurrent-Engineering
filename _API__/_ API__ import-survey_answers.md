# Survey Answers Import

Survey answers can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Survey Answers import file can be found in [Survey Answer - Fields](https://developer.xurrent.com/graphql/object/surveyanswer/#fields-1).

## CSV Example

```
Survey Response,Question,ID,Source,Source ID,Rating,Text
1,1,1,,,3.0,
1,2,2,,,,Please improve **search**!
```

[download CSV](https://developer.xurrent.com/csv/survey_answers.csv)
