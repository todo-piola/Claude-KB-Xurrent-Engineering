---
title: "More SLA Target Reports"
date: "September 19, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/more-sla-target-reports"
slug: "more-sla-target-reports"
---

# More SLA Target Reports

The following four reports have been added to the ‘Reports’ section of the Analytics console to help organizations keep track of their SLA performance, as well as the SLA performance of the service providers they rely on:

- Responses within Target Over Time
- Resolutions within Target Over Time
- Responses and Resolutions within Target Over Time
- SLA Responses

The ‘SLA Resolutions’ report already existed, which is why it is not included in this batch of new reports.

Users may notice that the ‘SLA Resolutions’ report looks very similar to the new ‘Resolutions within Target Over Time’ report.  The numbers in these two reports, however, are slightly different.  Specifically:

- the ‘SLA Resolutions’ report includes an affected SLA in the month in which the actual resolution was set, whereas
- the ‘Resolutions within Target Over Time’ report counts an affected SLA either in the month of the resolution target, or in the month in which the actual resolution was set, whichever comes first.

For example, let’s take a request created in January 2020 with an affected SLA resolution target in May 2020.  If this request was completed in March 2020, both the ‘SLA Resolutions’ report and the ‘Resolutions within Target Over Time’ report would count the request’s affected SLA in March 2020.  On the other hand, if this request was completed in June 2020, then the ‘SLA Resolutions’ report would include the request’s affected SLA in June 2020, while the ‘Resolutions within Target Over Time’ report would count it in May 2020.
