---
title: "Improved Find All Feature of Automation Rules"
date: "November 22, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/improved-find-all-feature-of-automation-rules"
slug: "improved-find-all-feature-of-automation-rules"
---

# Improved Find All Feature of Automation Rules

The find_all feature that was recently added to Xurrent’s Automation Rules functionality has been improved further.  There are now two flavors.  The one that already existed is used to look up all records from a field in which multiple records can be selected (see: [Find All Records in Multi-Value Custom Suggest Fields](https://www.xurrent.com/product-updates/find-all-records-in-multi-value-custom-suggest-fields)).  The following syntax can be used to do this:

- find_all(person, custom_fields.approvers)

The above example retrieves all person records that are selected in a custom field which ID is approvers.  What is new is that the find_all feature can now also be used to search through Xurrent to possibly find multiple records that match a search string.  To execute such a search, the following syntax can be used:

- find_all(person, `ashok.kumar@virtualsupport.com`)

This returns all matches that are found for the lookup value.  In this example, multiple values may be returned when a person record with the email address exists in multiple accounts and the account owner whose access rights are used to execute the automation rule has access to these accounts.

To reduce the results in this example to the person record that is registered in the Widget Data Center account, which account ID is wdc, the expression should be extended as follows:

- find_all(person, `ashok.kumar@virtualsupport.com`).select(account.id = ‘wdc’)

Or, to look up the organization that is linked to Ashok’s person record in Widget Data Center’s Xurrent account, the following expression can be used:

- find_all(person, `ashok.kumar@virtualsupport.com`).select(account.id = ‘wdc’)[first].organization

The result of this example looks as follows in the Notes section of a request:

