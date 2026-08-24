---
title: "Request Completion Duration Report"
date: "April 10, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/request-completion-duration-report"
slug: "request-completion-duration-report"
---

# Request Completion Duration Report

The report ‘Request Completion Duration’ has been added to allow support organizations to see how long it typically takes them to resolve requests.  This report simply looks at the time it takes for a request to get from being registered to being completed.  A 24×7 calendar is used for the calculations, so the service hours and support hours of the SLAs are ignored.

The duration calculations for this report are still slightly more complex than simply subtracting the moment of completion from the moment of creation.  That is because these values can vary for a request depending on the account that is looking at it.

For example, when a request was submitted by an enterprise employee to the IT department and the IT department passed it to an external provider the next day, then the creation of the request is one day later for the external provider than for the IT department.  And when the external provider completes the request, causing it to be returned to the IT department where it is completed the next day, then the completion duration is two days longer for the IT department than when the external provider opens this report.
