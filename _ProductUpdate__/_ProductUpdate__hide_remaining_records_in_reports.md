---
title: "Hide ‘Remaining Records’ in Reports"
date: "October 17, 2024"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/hide-remaining-records-in-reports"
slug: "hide-remaining-records-in-reports"
---

# Hide ‘Remaining Records’ in Reports

Reports in Xurrent over data that is grouped by a selected property can be configured to show only the top 3 (or other number) of records with that property. For example, the ‘Completed Requests by Site’ report can be grouped by ‘Category’, showing only the requests with the three most occurring categories within those sites.

To be complete, Xurrent also shows how many records exist outside those top 3 categories. Until now, this was called ‘Other’. This can, however, be confusing, as ‘Other’ is also the name of the category of requests that are Out of Scope. For this reason, these reports no longer show the word ‘Other’ in the legend, but ‘Remaining Records’.

When the user looking at the report does not want to see the records falling in this group of remaining records, they can just click the (in this case orange) dot in the legend. The numbers are then updated and only the real top 3 of categories is presented. Because Pie charts and Donut charts do not have a legend, this was not possible in those types of reports. Until now. A new option has been added to Metric reports that have the ‘Grouped By’ option applied: Do not show remaining records. After enabling it (it is disabled by default), the graph is updated to show the actual top 3 without the remaining records.

This new option is now also included in most Bar charts that do not have ‘Group by’ applied, but only if the chart is about numbers, not time, and only for single stack graphs. There, it is enabled by default.
