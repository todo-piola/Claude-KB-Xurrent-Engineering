# Reservation Offerings Import

Reservation Offerings can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Reservation Offerings import file can be found in [Reservation Offerings API - Fields](../../reservation_offerings/index.html#fields).

## CSV Example

```
"ID",Source,Source ID,Disabled,Name,Service Instance,Calendar,Time Zone,Initial Status,Min. Duration,Step Duration,Max. Duration,Preparation Duration,Min. Advance Duration,Max. Advance Duration,Multi-day,Filters,Configuration Items,Created At,Updated At
7,,,0,4me training environment,Service Management (Xurrent) Production,24x7 (Monday through Sunday),Central Time (US & Canada),confirmed,240,240,10080,,,,1,"","wdc-01
wdc-02",2020-07-09T20:34:33-05:00,2020-07-09T20:34:51-05:00
24,4me,,0,Conference Rooms,Customer Relationship Management (Siebel) Development & Test,"Monday through Friday, 9:00am until 5:00pm",Central Time (US & Canada),confirmed,60,10,120,20,15,30,0,"location,site,status","CNF00001
CNF00002
CNF00003
CNF00004",2020-07-10T20:24:05-05:00,2020-07-13T04:19:48-05:00
25,4me,,0,Pool Car,Pool Cars Houston,24x7 (Monday through Sunday),Central Time (US & Canada),confirmed,60,30,4320,30,120,144000,0,product,"CAR00018
CAR00024
CAR00027",2020-07-11T17:38:13-05:00,2020-07-11T18:17:53-05:00
```

[download CSV](https://developer.xurrent.com/csv/reservation_offerings.csv)
