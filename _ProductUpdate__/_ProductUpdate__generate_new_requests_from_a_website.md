---
title: "Generate New Requests From a Website"
date: "December 27, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/generate-new-requests-from-a-website"
slug: "generate-new-requests-from-a-website"
---

# Generate New Requests From a Website

Organizations that provide services to consumers, students, or citizens, often use their website as a portal for answering questions or logging requests.  Registering these people and their requests in Xurrent enables these organizations to apply Xurrent’s service management capabilities to these issues, allowing for easier communication, the possibility to assign requests to specialists within the organization, reporting, and more.

It was already possible for [people to register themselves via Xurrent Self Service](https://www.xurrent.com/product-updates/allow-people-to-register-themselves), with [OpenID Connect](https://www.xurrent.com/product-updates/support-for-openid-connect) or by [sending an email](https://developer.xurrent.com/v1/requests/mail/) to the right Xurrent email address, provided of course that this is allowed in the settings.  Now it is also possible for a website to collect a user’s email address and other information and send that as an email to Xurrent, generating a person record if that customer is not yet known, and a new request.

To support this new functionality, a new parameter for sending email using the [Mail API](https://developer.xurrent.com/v1/requests/mail/) has been added to this API: the #from parameter.  An option to allow for the use of this new parameter has been added to the ‘Email Policy’ section of the Settings console for Inbound Email.

Ticking the`Allow email parameter #from` box in these settings expands this option.  The `Senders`field becomes visible, in which one or more email addresses that are allowed to send email with the #from email parameter can be entered.  In the `Authentication token(s)` field one or more authentication tokens must be entered.  Inbound email with a #From parameter is rejected if the sender and / or authentication token is not registered in these settings.

The example below shows how these parameters can be used for inbound emails.

