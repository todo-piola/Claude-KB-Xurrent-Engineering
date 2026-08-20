---
title: "Filter Products and CIs by Category Rule Set"
date: "March 9, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/filter-products-and-cis-by-category-rule-set"
slug: "filter-products-and-cis-by-category-rule-set"
---

# Filter Products and CIs by Category Rule Set

A useful filter has been added for configuration managers.  The new filter is called ‘Product category rule set’.  This sounds fairly complicated, but Xurrent account administrators will recognize the term ‘rule set’ from the ‘Product Categories’ section of the Settings console.  That section is used by support organizations to disable some of Xurrent’s default product categories and add custom ones as needed.

When adding a new product category, an administrator needs to select a rule set for it.  A rule set dictates which fields are available in product and configuration item (CI) records that are linked to the [product category](https://help.xurrent.com/help/product_category_fields/).

One of the following rule sets can be selected for a new product category:

- Physical Asset
- Logical Asset with Financial Data
- Logical Asset without Financial Data
- Server
- Software
- Software Distribution Package

But there is also one rule set that cannot be linked to a new product category.  That is the rule set ‘License Certificate’.  This rule set dictates which fields are available when a new license certificate CI is registered for a software product.

So, in total there are 7 rule sets.  Being able to filter CI views and reports by one or more rule sets can be quite useful.  The new filter makes it possible, for example, to exclude all software CIs and all license certificate CIs from a report.

