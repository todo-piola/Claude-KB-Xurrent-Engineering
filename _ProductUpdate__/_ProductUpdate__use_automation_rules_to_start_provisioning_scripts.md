---
title: "Use Automation Rules to Start Provisioning Scripts"
date: "March 26, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/use-automation-rules-to-start-provisioning-scripts"
slug: "use-automation-rules-to-start-provisioning-scripts"
---

# Use Automation Rules to Start Provisioning Scripts

Automation rules are now able to call [webhooks](https://developer.xurrent.com/v1/webhooks/), enabling these webhooks to deliver a custom payload to a target server.  Why this is such a powerful new feature is best explained with an example.

Let us assume an enterprise organization has a service that its employees use to submit their expense reports.  Requests to gain access to the Expense Reporting service can be submitted by any employee using Xurrent Self Service.  The request template the enterprise has made available for this is linked to a change template with two task templates, which together define a 2-step workflow.  The first step is an approval task for the manager of the person for whom the request was submitted.  The second step is an implementation task, which will automatically be set to the status ‘Assigned’ as soon as the first task has reached the status ‘Approved’.

The second task could, for example, be assigned to the security team, where a specialist would manually provide the requested access.  Xurrent’s automation rules now make it much easier to automate this step, thanks to the new capability of defining a customized payload which an automation rule can ask a webhook to deliver to its target server.

Before defining the automation rule for the second task, it is important to first create the webhook it will call.  Administrators can do this in the ‘Webhooks’ section of the Settings console.  The event type automation_rule needs to be selected for this webhook.  This new event type ensures that the webhook can be selected in an automation rule.

Once the webhook has been created, the automation rule for the second task template can be created.  The action of this automation rule is to call the webhook and to tell it to include two pieces of information in its payload:

- the value that is in the Authentication ID field of the person record that is selected in the Requested for field of the first request that is linked to the change of the task to which the automation rule is linked, and
- the record ID of the task to which the automation rule is linked.

When this automation rule is triggered and its condition is met, the automation trail can be accessed to check whether the webhook was called successfully.  The automation trail can be opened from the task by clicking on the **Actions** toolbar button and selecting the option ‘Automation Trail…’ from the Actions menu.  From there, the automation trace of the rule’s last execution can be opened.

The green task icon in the automation trace indicates that the condition of the automation rule was met.  Clicking on the webhook icon on the right opens a preview of the webhook.  From this preview, it is possible to open the last [webhook delivery](https://www.xurrent.com/product-updates/introducing-webhook-deliveries) in a separate browser tab with a Ctrl+click on its ID.

The webhook delivery contains all the details of the webhook request, including its payload.

Both the person_auth_id and the task_id expressions are included in the payload.  The person_auth_id can be used by the script on the target server to give the right person access to the Expense Reporting service.  After the script has provided this person the requested access, it can use the task_id to tell Xurrent’s [Task API](https://developer.xurrent.com/v1/tasks/) to set the status of the task to ‘Completed’.  That will automatically cause the change and the request to be completed.  And when the request is completed, Xurrent generates a notification to let the requester know that (s)he is now able to submit expense reports.
