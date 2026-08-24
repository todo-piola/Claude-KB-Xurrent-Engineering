# Shop Article Categories Import

Shop article categories can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Shop Article Categories import file can be found in [Shop Article Categories API - Fields](../../shop_article_categories/index.html#fields).

## CSV Example

```
"ID",Source,Source ID,Name,Picture URI,Short Description,Full Description,Parent
,4me,,Equipment,https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_categories/original/equipment.svg,All electronic equipment provided by Widget Data Center.,This category contains all kinds of electronic equipment provided by Widget Data Center. This is your one-stop shop for every device required to make your day productive.,
,4me,,Computers,https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_categories/original/computers.svg,All computers provided by Widget Data Center.,This category contains every computer imaginable provided by Widget Data Center. This is your one-stop shop for every device required to make your day productive.,Equipment
,4me,,Desktops,https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_categories/original/desktops.svg,All desktops provided by Widget Data Center.,This category contains every desktop imaginable provided by Widget Data Center. This is your one-stop shop for every device required to make your day productive.,Computers
,4me,,Laptops,https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_categories/original/laptops.svg,All laptops provided by Widget Data Center.,This category contains every laptop imaginable provided by Widget Data Center. This is your one-stop shop for every device required to make your day productive.,Computers
,4me,,Cables,https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_categories/original/cables.svg,,,Equipment
,4me,,Internet Access,https://4me-demo-assets.s3-accelerate.dualstack.amazonaws.com/avatars/shop_article_categories/original/internet_access.svg,Upgrade or downgrade your internet connection speed.,,Service Delivery @widget
```

[download CSV](https://developer.xurrent.com/csv/shop_article_categories.csv)
