# Reservations Import

Reservations can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Reservations import file can be found in [Reservations API - Fields](../../reservations.html#fields).

## CSV Example

```
"ID",Source,Source ID,Reservation Offering,Name,Status,Request,Created By,Person,Configuration Item,Preparation Start At,Start At,End At,Description,Created At,Updated At
5,,,Conference Room Reservation,canceled,Conference Rooms,80160,beatrice.baldwin@widget.com @widget,beatrice.baldwin@widget.com @widget,CNF00002,2020-07-13T13:55:00Z,2020-07-13T14:15:00Z,2020-07-13T15:15:00Z,,2020-07-10T20:28:00-05:00,2020-07-10T20:29:35-05:00
6,,,Reserve a pool car,confirmed,Pool Car,80162,beatrice.baldwin@widget.com @widget,beatrice.baldwin@widget.com @widget,CAR00024,2020-07-13T14:30:00Z,2020-07-13T15:00:00Z,2020-07-13T23:00:00Z,,2020-07-11T18:32:42-05:00,2020-07-11T18:32:46-05:00
```

[download CSV](https://developer.xurrent.com/csv/reservations.csv)
