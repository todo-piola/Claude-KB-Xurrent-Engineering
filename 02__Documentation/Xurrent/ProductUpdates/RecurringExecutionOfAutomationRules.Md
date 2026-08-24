---
title: "Recurring Execution of Automation Rules"
date: "November 24, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/recurring-execution-of-automation-rules"
slug: "recurring-execution-of-automation-rules"
---

# Recurring Execution of Automation Rules

[Automation rules](https://www.xurrent.com/product-updates/introducing-automation-rules) now allow delayed rules to be executed multiple times in a single automation chain.  This also allows for the use of loops in automation rules, that can be used to send daily reminders for approval tasks, for example.

As an example, two automation rules called ‘Reminder Loop Start’ and ‘Reminder Loop’ are created on a [task template](https://www.xurrent.com/blog/add-automation-rules-to-task-templates).  The first one is executed as soon as the approval task is assigned. After 24 hours, the second automation rule is called.

This second automation rule starts itself after 24 hours, creating a loop.  The loop is broken as soon as the approval task’s status is no longer ‘Assigned’, or when the maximum of 120 executions of the rule in the same automation chain has been reached.  Another restriction is set on the delay time: the last execution of the recurring rule must be at least 23 hours ago.

