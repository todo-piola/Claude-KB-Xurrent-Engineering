---
title: "Decide if Customer’s Specialists Can See Requests"
date: "December 4, 2019"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/decide-if-customer-specialists-can-see-requests"
slug: "decide-if-customer-specialists-can-see-requests"
---

# Decide if Customer’s Specialists Can See Requests

An advanced SLA feature has become available for enterprises with multiple support domain accounts, for example for their IT, HR and Finance departments.  This feature becomes available when one support domain registers an SLA for another support domain of the same enterprise.  This feature is best explained with an example.

Let’s assume that the Human Resources department of Widget North America takes care of all employees of the Widget Data Center organization.  Both organizations have their own support domain account under the Widget International directory account.  Because the HR department provides the payroll service to Widget Data Center, the service level manager of the HR department registers this SLA.  When the service level manager selects the Widget Data Center organization in the Customer field of the SLA, the Customer account field now becomes available.

This new field allows the service level manager of the HR department to select either the support domain of the customer (this is the default), or the support domain of the provider (i.e. the HR department).

If the SLA is saved with the default option, i.e. with Widget Data Center selected in the Customer account field, then the SLA’s coverage will need to be set by a service level manager of the Widget Data Center account.  More importantly, though, when a Widget Data Center employee submits a request for the Payroll service, this request will be assigned to a team in the HR department’s support domain, but Widget Data Center specialists will be able to see this request.

Because requests that concern the Payroll service are likely to contain very personal information, this is probably not desirable.  That is why the service level manager of the HR department will select the other option that is available in the Customer account field, i.e. the Widget North America – HR support domain account.

This option ensures that only the service level managers of the HR department will be able to update the parts of the SLA that normally the service level managers of the customer would maintain.  And, more importantly again, requests that affect this SLA will not become visible to the specialists (nor auditors or administrators) of the customer.

Note that the customer account of an SLA can only be set when the SLA is being created.  Once an SLA has been saved for the first time, it is no longer possible to change the customer account.  If a mistake was made, this can be resolved by expiring the SLA and registering a new one.
