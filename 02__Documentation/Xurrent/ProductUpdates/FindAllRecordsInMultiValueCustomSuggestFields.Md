---
title: "Find All Records in Multi-Value Custom Suggest Fields"
date: "October 25, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/find-all-records-in-multi-value-custom-suggest-fields"
slug: "find-all-records-in-multi-value-custom-suggest-fields"
---

# Find All Records in Multi-Value Custom Suggest Fields

A few releases ago, it became possible to use the UI extension functionality to [add custom suggest fields in which multiple values can be selected](https://www.xurrent.com/blog/select-multiple-values-in-custom-suggest-fields).  The automation rules now provide the ability to not only retrieve the IDs of all records selected in such custom fields, but also to convert these IDs to actual records so they can be used in automated actions.  This can be done using the following expression:

- find_all(record_type, custom_multi_suggest_field_expression)

For example, let’s take a request that has a UI extension with a suggest field in which multiple people are selected.

An automation rule can now be used to look up the people selected in the request.  The automation rule can then relate these people to an approval task of the change that is linked to the request.  And the automation rule can also update the number of required approvals in this task to make sure they all need to provide their approval, after which the rule can cause the approval task’s status to be updated to ‘Assigned’.

When the automation rule has done its job, the approvers will see the updates in the approval task when they open it.

Note that the following expression was already available for retrieving the record from a custom field in which only a single record can be selected:

- find(record_type, custom_suggest_field_expression)
