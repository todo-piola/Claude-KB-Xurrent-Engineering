# Shop Articles Import

Shop articles can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Shop Articles import file can be found in [Shop Articles API - Fields](../../shop_articles/index.html#fields).

## CSV Example

```
"ID",Reference,Product,Fulfillment Template,Delivery Duration,Requires Shipping,Calendar,Time Zone,UI Extension,Service Offerings,Created At,Updated At,Disabled,Source,Source ID,Name,Short Description,Full Description,Picture URI,Start At,End At,Max. Quantity,Price,Price Currency,Recurring Price,Recurring Price Currency,Recurring Period
2,DellM4400,Dell Precision M4400 Laptop PC,1401,8640,1,24x7 (Monday through Sunday),Central Time (US & Canada),,Bronze Personal Computing,2022-11-24T08:11:21-06:00,2022-11-24T08:11:21-06:00,0,,,Dell Precision M4400,"Dell’s most powerful 17"" mobile workstation with AI.","Dell’s most powerful 17"" mobile workstation with AI. Featuring up to Intel® Core® or Xeon® processors, NVIDIA® professional graphics and Dell Optimizer for Precision.",https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_accounts/original/Dell Precision M4400 Laptop PC.png,,,1,2350.0,usd,,,
3,DellT5400,Dell Precision T5400 Workstation,1401,8640,1,24x7 (Monday through Sunday),Central Time (US & Canada),,Bronze Personal Computing,2022-11-24T08:11:21-06:00,2022-11-24T08:11:21-06:00,0,,,Dell Precision T5400 Workstation,Brainpower that matches yours: The latest Intel® Xeon® processor powers your most demanding applications.,"Brainpower that matches yours: The latest Intel® Xeon® processor powers your most demanding applications. Now featuring a new generation of single-socket architecture with up to 18 cores, you can extract maximum performance for your biggest ideas.

Accelerate every project: Run your software as fast as possible and get real-time results thanks to this memory expandable machine with up to 512GB of 2666MHz RDIMM ECC memory (not available with Core X CPUs).

Drown out distraction: Focus on your tasks with the workstation that’s quieter than ever. A new multichannel thermal design delivers advanced cooling and acoustics.",https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_accounts/original/Dell Precision T5400 Workstation.png,,,5,1899.0,usd,,,
```

[download CSV](https://developer.xurrent.com/csv/shop_articles.csv)
