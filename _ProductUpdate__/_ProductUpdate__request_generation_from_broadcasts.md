---
title: "Request Generation From Broadcasts"
date: "November 15, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/request-generation-from-broadcasts"
slug: "request-generation-from-broadcasts"
---

# Request Generation From Broadcasts

Whenever a major incident happens that affects multiple users, it is possible in Xurrent to create a [broadcast](https://www.xurrent.com/product-updates/broadcast-a-message-to-your-customers) that is sent to specific groups of users to inform them about the unavailability or degradation of a service or service instance.  In such cases, multiple requests with the category incident are likely created, and grouped into a request group.  End users can now subscribe to a request group directly from a broadcast in Xurrent Self Service.  This ensures that they are notified when the major incident has been resolved.

For this, the Request group field has been added to the Broadcast form.  It is available when any of the first three groups of people is selected in the Visible for field:

- All people of the account
- [People covered for any of our service instances](https://www.xurrent.com/product-updates/broadcasts-to-all-users)
- People covered for selected service instances

This broadcast in Xurrent Self Service now comes with a button **I’m Also Affected**, which, if clicked, asks the end user to confirm if he or she also wants to register a request for this issue.  After clicking the **Submit**button, the request is generated and automatically linked to the request group.

When the status of the request group is set to ‘Completed’, the End field of the broadcast is automatically set to the current date and time, so the broadcast ends as well.
