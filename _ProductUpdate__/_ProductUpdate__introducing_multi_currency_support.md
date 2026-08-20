---
title: "Introducing Multi-Currency Support"
date: "August 2, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-multi-currency-support"
slug: "introducing-multi-currency-support"
---

# Introducing Multi-Currency Support

As part of our [financial management](https://www.xurrent.com/features/financial-management) initiative, another important milestone has been reached in the form of multi-currency support.  Since many organizations have international offices, hire staff abroad and acquire assets in multiple currencies, [financial managers](https://www.xurrent.com/product-updates/introducing-the-financial-manager-role) want to be able to record these amounts in their original currencies while being able to aggregate them in the currency that the organization uses for financial reporting.

Organizations can now enter financial amounts in nearly 40 of the world’s most widely used currencies.  Xurrent instantly converts these amounts to the currency that is specified in the organization’s Xurrent account and adds the converted amount so that it is available for reporting.  The following record types have multi-currency support:

- **Person**: Cost per hour
- **Skill Pool**: Cost per hour
- **CI**: Purchase value, Salvage value
- **Project**: Value
- **Invoice**: Amount
- **Time Entry**: Cost

In View mode of records, all fields that show a value with a currency also show the value in the currency of the account, if the currency of the value is different.

All reports containing financial information, including the project management reports, present those amounts in the currency of the account in which the report is opened.  So, if a support domain account has its currency set to Euros in the ‘Account Settings’ section of the Settings console, reports opened in that account show all amounts in Euros, even if some of these amounts were entered in British pounds, Danish kroner, Swiss francs or US dollars.

For example, when the report ‘Cost of Time Spent by Person’ is opened in the support domain account of Widget Europe’s IT department, Radosław Wiśniewski’s costs are displayed in Euros, even though his ‘Cost per hour’ was registered in Polish złoty.

When the same report is opened in the directory account of the US-headquartered Widget International organization, the amounts are presented in US dollars.

If someone with a Financial Manager role drills down on these reports, the time entries will show the individual costs in the original currency.  Values in the columns of views are always presented in their original currency.

Invoices can also be registered in the currency stated on the invoice.  When invoices are listed in, for example, a project record, they are listed with their respective currencies.  Totals are always displayed in the currency of the account in which the record is opened.

To convert an amount to a different currency, Xurrent looks up the foreign exchange rate on the date that is applicable to the amount.  Depending on the record type, Xurrent uses the following dates:

- **Invoice**: the date specified in the Invoice date field
- **Project**: the date on which the amount was entered
- **Time Entry**: the date specified in the Date field
- **Configuration Item**: the date specified in the Start date field

The Xurrent REST API and the Xurrent GraphQL API, as well as the Import functionality, also support the ability to input financial amounts in different currencies.  For exports, an extra column has been added to specify the currency next each column that contains financial amounts.

