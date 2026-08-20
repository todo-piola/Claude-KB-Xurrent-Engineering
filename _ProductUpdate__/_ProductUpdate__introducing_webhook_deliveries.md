---
title: "Introducing Webhook Deliveries"
date: "February 23, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-webhook-deliveries"
slug: "introducing-webhook-deliveries"
---

# Introducing Webhook Deliveries

For developers who build integrations with Xurrent, a new section has become available in the Settings console.  This new section is called ‘Webhook Deliveries’.  To access this section quickly, just type  web  in the Search box after clicking on the Settings console icon.

Each time a [webhook](https://developer.xurrent.com/v1/webhooks/) tries to deliver its payload to a URI (a target server), an entry is added to this section.  These webhook delivery records are useful because they provide a lot of information about when the webhook attempted to deliver its payload, what was included in the payload, whether the payload was successfully delivered and what the response was from the target server.

The value of this new functionality quickly becomes apparent after an administrator has received an exception email from Xurrent.  When the webhook is opened, a link is now provided to the last webhook delivery.

Clicking on the link opens the webhook delivery.

Probably the most useful feature for developers is the ability to get the webhook to send its payload again, for example, after the integration has been corrected.  All it takes, is a click on the **Redeliver** button.
