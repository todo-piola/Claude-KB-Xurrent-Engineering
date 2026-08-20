---
title: "Waiting for Customer Follow-Ups"
date: "October 3, 2023"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/waiting-for-customer-follow-ups"
slug: "waiting-for-customer-follow-ups"
---

# Waiting for Customer Follow-Ups

If a request has already been sitting in the status ‘Waiting for Customer’ for some time and no response has been provided by the requester, the support organization typically would like to remind the requester to respond. If the requester still does not respond, the support organization can complete the request indicating that there was no response, informing the requester that they can always reopen the request when the request has time to respond. These follow-ups can now be configured in Xurrent in the newly added ‘Waiting for Customer Follow-Ups’ section of the Settings console and related to specific service offerings.

To do this, only the number of business days (as determined from the support hours of the affected SLA, which takes this from the service offering) needs to be entered for each rule in a Waiting for Customer Follow-Up configuration. Additional rules can be created by pressing the green **Add Notification Rule** button. Up to five notifications can be configured this way.

After associating the above configuration to one or more service offerings by selecting it in the `Follow-up` field, the requester will receive email reminders based on the new email template ‘Waiting for Customer Follow-Up’ after each number of business days configured in these rules.

Enabling the ‘Auto-complete’ option in the Waiting for Customer Follow-Up configuration will automatically complete the request in the account that was waiting for the customer, if no reply was given after the number of business days defined in the last rule. The email that is sent to the customer is based on the email template ‘Waiting for Customer Auto Completion’.

