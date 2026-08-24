---
title: "Update Automation Rules After Template Rule Update"
date: "September 10, 2024"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/update-automation-rules-after-template-rule-update"
slug: "update-automation-rules-after-template-rule-update"
---

# Update Automation Rules After Template Rule Update

Request templates, workflow templates, task templates, and other templates in Xurrent are used to make sure that the requests, workflows, tasks etc. created from them all have the same relevant properties. Automation rules defined on these templates also work on all the records generated from those templates.

When a request is created from a request template, for example, the automation rule related to that request functions the way it was set up at the moment the request was registered. When the automation rule is changed, for whatever reason, only requests registered from that template from that moment on will be associated with that new version of the automation rule. In many cases, this makes sense: the same applies to the pre-filled fields and options on the template. In other cases, though, it would be helpful if the new version of the automation rule could be applied to all the associated automation rules on already registered requests from that request template. This is now possible.

