---
title: "Provider Not Accountable"
date: "April 20, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/provider-not-accountable"
slug: "provider-not-accountable"
---

# Provider Not Accountable

Service level agreements (SLAs) are established between service providers and customers to agree on a minimum service level.  Whenever a request is registered, the clock of the [affected SLAs](https://www.xurrent.com/blog/improved-asla-generation) starts running, so Xurrent can calculate whether the agreements are met or violated.  There are, however, cases where a provider does not want to be held [accountable for SLA breaches](https://www.xurrent.com/product-updates/stop-sla-clock-when-msp-passes-request-to-another-msp).  This can be the case, for example, when a workflow has to wait for an approval of the customer.  It is now possible for a provider to stop the SLA clock under certain conditions.

A new flag ‘`provider_not_accountable`‘ has been introduced, that (for now) can only be accessed by automation rules (on the request template or on an approval task), UI extensions and APIs.  The following example shows an automation that stops the clock.

When the clock is stopped (or started), a system note is generated.  In the ‘Affected SLAs’ section it is also clearly visible if the clock was stopped and the provider is not accountable.

To restart the clock after the task has been approved, rejected or canceled, another automation rule can be created to reset the flag `provider_not_accountable` to false.

Whenever a request that is included in an SLA report in the Analytics console had its SLA clock stopped, a line is added to the report, stating the number of requests for which this was the case.  Drilling down into this number displays the affected requests.

To be able to manually look up this information, two new filters have been added to the ‘Requests’ section of the Records console, and to the view of the affected SLAs.  ‘Provider Not Accountable’ shows records where the provider is not accountable now, and ‘Provider Was Not Accountable’ shows records where the clock had stopped at some point.
