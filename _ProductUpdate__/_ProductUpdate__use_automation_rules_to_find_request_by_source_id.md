---
title: "Use Automation Rules to Find Request by Source ID"
date: "June 4, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/use-automation-rules-to-find-request-by-source-id"
slug: "use-automation-rules-to-find-request-by-source-id"
---

# Use Automation Rules to Find Request by Source ID

The`find(request, …)`and`find_all(request, …)`operations of automation rules now also look through the Source ID field of requests.  This means that these operations can now also be used to find a request that has a specific value in its Source ID field.  This can be useful, for example, when data needs to be retrieved from a request that was generated in Xurrent by an external system and only the unique identifier from the external system is known.

The example above will return the request ID of the first request which Source ID field value matches the value in the custom field`incident_number`.
