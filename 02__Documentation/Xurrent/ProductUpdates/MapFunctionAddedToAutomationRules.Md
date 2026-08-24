---
title: "Map Function Added to Automation Rules"
date: "December 18, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/map-function-added-to-automation-rules"
slug: "map-function-added-to-automation-rules"
---

# Map Function Added to Automation Rules

The `map` function is new to the [automation rules](https://www.xurrent.com/product-updates/introducing-automation-rules).  It can be used to work on arrays, just like other array functions like `select`, `reject`, `count`, etc.  Here is an example of how the `map` function can be used in an automation rule expression:

This expression returns the first person record that is linked as a user to the first configuration item linked to each task of the change.  This list of people can then, for example, be added as approvers to an approval task.

But the `map` function can also be used in combination with the `find_all` function to retrieve all records of a specific record type that are related to the records that are selected in a field in which multiple records can be selected.

This sounds pretty complex, so it is best illustrated with a simple example.  Let’s assume a request template has been prepared for ordering equipment and this request template has a UI extension in which multiple cost centers can be selected.  And let’s assume that each of these cost centers has an approver linked to it.  The new [`find_all`](https://www.xurrent.com/product-updates/find-all-records-in-multi-value-custom-suggest-fields) feature makes it possible to apply an automation rule to the first task template of the change template that is linked to the request template to ensure that the approvers of the selected cost centers are linked as approvers to the second task of the change workflow.

Below is what this automation rule would look like:

