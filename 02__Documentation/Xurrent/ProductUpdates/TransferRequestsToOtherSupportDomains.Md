---
title: "Transfer Requests to Other Support Domains"
date: "November 1, 2023"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/transfer-requests-to-other-support-domains"
slug: "transfer-requests-to-other-support-domains"
---

# Transfer Requests to Other Support Domains

Sometimes, when a user submits a request, they select the wrong service within the wrong [support domain](https://www.xurrent.com/product-updates/create-support-domain-accounts). This can happen, for example, when they receive a spam email. Instead of registering a request in the Security account, they select the Email service of the IT account. It can also happen, that a request was registered within the IT account when it was actually supposed to be registered in an HR account, which has ‘[strong privacy](https://www.xurrent.com/product-updates/strong-privacy)’ enabled. Simply completing the request and submitting a new request on the proper support domain is then not always enough, as the completed request will then still be visible by specialists of the IT account. It is now possible to easily redirect a request to another support domain within the same directory structure.

This new feature is accessible via the **Forward** button above the request, which is available depending on the access the specialist has to the request. From here, it is now no longer only possible to forward a request to another team (‘Reassign’), but also to transfer it to another subdomain account (‘Transfer’).

After selecting ‘Transfer’, the specialist can choose the correct account and has the option to add a note. After pressing the **Forward** button, the request is sent to the first line support team of the target account and removed from the source account. This includes affected SLAs, audit lines, custom fields, and any other data that is no longer relevant to the request. The category of the request is updated to ‘Other’.

A request may only be transferred if:

- The request is only linked to a single request account
- The request is not linked to a workflow or problem
- The request is not a group or grouped into another request
- The category of the request is other then ‘reservation’, ‘order’, or ‘fulfillment’
- The request is not linked to a product backlog or sprint backlog item
