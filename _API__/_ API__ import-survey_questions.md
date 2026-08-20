# Survey Questions Import

Survey questions can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Survey Questions import file can be found in [Survey Question - Fields](https://developer.xurrent.com/graphql/object/surveyquestion/#fields-1).

## CSV Example

```
Survey,ID,Source,Source ID,Disabled,Question,Guidance,Type,Position,Weight
My Survey,1,,,0,How do you rate us?,,star_rating,1,100
My Survey,2,,,0,Anything else to add?,Any extra information you wish to share with us?,text,2,100
```

[download CSV](https://developer.xurrent.com/csv/survey_questions.csv)
