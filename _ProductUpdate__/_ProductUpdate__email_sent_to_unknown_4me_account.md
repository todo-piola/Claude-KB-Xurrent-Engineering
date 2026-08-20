---
title: "Email Sent to Unknown Xurrent Account"
date: "February 1, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/email-sent-to-unknown-4me-account"
slug: "email-sent-to-unknown-4me-account"
---

# Email Sent to Unknown Xurrent Account

When someone sends an email to the inbound email address of an organization’s Xurrent account, the [Xurrent Mail API](https://developer.xurrent.com/v1/requests/mail/) will process it.  In most cases, this results in a new request getting generated and the sender receiving a confirmation email that includes a link to the new request.

But when a message was addressed to a Xurrent account that does not exist, the sender would not receive an indication that something went wrong.  To ensure that people are made aware that their email was sent to an incorrect Xurrent email address, Xurrent now returns a bounce message to notify the sender that the email did not get processed.

Xurrent returns such a bounce message when an email was sent to:

- an email address that does not belong to any Xurrent account
- the email address of a Xurrent account that has been disabled
- the email address of a Xurrent directory account (because requests, tasks, etc. are never registered in a directory account)
- a team mailbox, but a team with that email address does not exist or is disabled

When an email that was sent to a [team mailbox](https://www.xurrent.com/blog/give-your-teams-an-email-address) failed to process, this failure also gets logged in the ‘Inbound Email’ section of the Settings console of the Xurrent account that was specified in the email address.
