---
title: "Trigger a Webhook When a Project Task is Deleted"
date: "November 14, 2019"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/trigger-a-webhook-when-a-project-task-is-deleted"
slug: "trigger-a-webhook-when-a-project-task-is-deleted"
---

# Trigger a Webhook When a Project Task is Deleted

More and more provider organizations are integrating their Xurrent account with their billing system.  They may, for example, create an item in their invoicing tool for each project task.  That allows them to sync the Xurrent time entries of their project tasks.  But if a project manager removes a project task from Xurrent, its corresponding item in the billing system would stay open.

To prevent this, it is now possible to set up a [webhook](https://developer.xurrent.com/v1/webhooks/) that triggers a script to remove the item from the billing system after the project task for which it was generated has been deleted in Xurrent.

