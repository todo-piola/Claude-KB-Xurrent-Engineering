---
title: "Add Tasks to Workflows Dynamically"
date: "March 14, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/add-tasks-to-workflows-dynamically"
slug: "add-tasks-to-workflows-dynamically"
---

# Add Tasks to Workflows Dynamically

It is now possible to add tasks to a workflow dynamically, using [automation rules](https://www.xurrent.com/product-updates/introducing-automation-rules).  This provides organizations with even more [flexibility](https://www.xurrent.com/blog/workflow-control-exception-flows)in deciding which tasks should be part of a workflow under different conditions.

As an example, a simple UI extension has been added to the workflow template ‘Prepare services for new employee’ to indicate in which team the new employee will be working.  New employees that will be part of the End-User Support team in Houston should be provided with an external hard disk.  The following automation rule example takes care of this:

As soon as the task ‘Prepare new PC’ is assigned and if the selected team was ‘End-User Support, Houston’, the new task ‘Provide external hard disk drive to user’ is added to the existing tasks in the workflow.  Subsequently the task ‘Prepare new PC’ is set as predecessor of this new task.

