---
title: "Affected SLAs No Longer Affected"
date: "September 26, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/affected-slas-no-longer-affected"
slug: "affected-slas-no-longer-affected"
---

# Affected SLAs No Longer Affected

When a request is initially linked to a [service instance](https://help.xurrent.com/help/service_instance/), but is later linked to another service instance that is not hierarchically below the previous one, the [affected SLA](https://help.xurrent.com/help/affected_sla/) for the first service instance is no longer considered ‘affected’.  This is not uncommon.  For example, when someone is no longer able to access the SAP production environment, a request may be registered that is linked to this service instance.  A specialist may later determine, however, that the issue is caused by a Wi-Fi outage in one of the office buildings.  At this point, the specialist will update the service instance of the request to the building’s Wi-Fi network.  This causes the affected SLA that is linked to the request for the SAP production environment to be marked as ‘SLA Not Affected’.

A support organization may want to see if it might be able to improve the initial service instance selection for its requests.  To facilitate this, it would be helpful to have a report that includes all affected SLAs that were later found to be unrelated to the request.  This report is now available in the ‘Reports’ section of the Analytics console.  It is called ‘Affected SLAs No Longer Affected’.

