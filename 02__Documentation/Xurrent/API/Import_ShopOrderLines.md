# Shop Order Lines Import

Shop order lines can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Shop Order Lines import file can be found in [Shop Order Lines API - Fields](../../shop_order_lines/index.html#fields).

## CSV Example

```
"ID",Source,Source ID,Requested For,Shop Article,Name,Fulfillment Template,Status,Quantity,Price,Price Currency,Recurring Price,Recurring Price Currency,Recurring Period,Ordered At,Order,Fulfillment Task,Fulfillment Request,Delivery address,Delivery City,Delivery State,Delivery Zip,Delivery Country,Completed At,Created At,Updated At
1,,,heinrich@widget.com @widget,DellM4400,Dell Precision M4400,1401,in_cart,1,2350.0,usd,,,,,,,,,,,,,,2022-11-24T08:11:22-06:00,2022-11-24T08:11:22-06:00
4,4me,,beatrice.baldwin@widget.com @widget,HPC6730s,HP Compaq 6730s,1401,fulfillment_pending,3,799.0,usd,,,,2022-11-29T04:20:32-06:00,90658,32070,,1919 Briar Oaks Lane,Houston,TX,77027,US,,2022-11-29T04:20:13-06:00,2022-11-30T03:57:05-06:00
```

[download CSV](https://developer.xurrent.com/csv/shop_order_lines.csv)
