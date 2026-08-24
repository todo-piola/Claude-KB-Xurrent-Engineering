---
title: "Use Source & Source ID to Update Requests with Mail API"
date: "October 1, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/use-source-source-id-to-update-requests-with-mail-api"
slug: "use-source-source-id-to-update-requests-with-mail-api"
---

# Use Source & Source ID to Update Requests with Mail API

The [Mail API parameters](https://developer.xurrent.com/v1/requests/mail/) source and sourceID are now also used to determine whether a new request needs to be registered for an email that was sent to Xurrent, or a note needs to be added to an existing request.

This can be useful when an external event management system or another service management application initially sent an email to Xurrent with the source and sourceID parameters included at the top of the email body.  If the external system subsequently sends another email to Xurrent with the same source and sourceID, the Xurrent Mail API will no longer create a new request, but instead add the body content and attachments as a new note to the previously generated request.

This new feature of Xurrent’s Mail API will prevent multiple requests from being generated for the same issue.  It is also available for updates of existing problems, releases, changes, change tasks, projects and project tasks. More details about this new feature can be found in the [Xurrent Mail API documentation](https://developer.xurrent.com/v1/requests/mail/).
