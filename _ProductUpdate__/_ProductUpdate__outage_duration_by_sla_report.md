---
title: "Outage Duration by SLA Report"
date: "September 23, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/outage-duration-by-sla-report"
slug: "outage-duration-by-sla-report"
---

# Outage Duration by SLA Report

Support organizations are now able to add another interesting report to their SLA tracking [dashboards](https://www.xurrent.com/product-updates/build-your-own-dashboards).  The new report that has been added to the ‘Reports’ section of the Analytics console is called ‘Outage Duration by SLA’.  It shows the cumulative outage duration for the SLAs that were affected during a specific date range.

This report takes into account only the [affected SLAs](https://help.xurrent.com/help/affected_sla/) which impact is set to ‘Top’.  The affected SLAs also need to be registered in, or provided to, the account from which the report is opened (i.e. the account selected in the [Account Switcher](https://help.xurrent.com/help/accounts/)).  To avoid adding up the outage duration of requests that belong to the same request group (and therefore all have the same outage duration), the report considers only the affected SLAs of the last request of each top-impact request group.

For an outage to be included in the report, its downtime end needs to fall within the date rage of the report.

Filtering this report by customer or customer account makes it possible to quickly obtain an overview of the outages a customer experienced and the services that were affected.
