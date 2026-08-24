---
title: "Billing Integration: Charges"
date: "March 29, 2023"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/billing-integration-charges"
slug: "billing-integration-charges"
---

# Billing Integration: Charges

Since the start of this year, Xurrent® has introduced [several enhancements](https://www.xurrent.com/blog/billing-integration-billing-identifiers) to make it easier for managed service providers to use the Xurrent data to generate invoices for their customers.  One of these was the possibility to relate [effort classes](https://www.xurrent.com/blog/introducing-billing-integration-effort-classes) to a specific service offering, in order to be able to identify the types of activities that were performed and relate these to a contract with a customer (SLA).  It is now possible to add rates for these activities to the service offerings.

A ‘Financial Details’ section has been added to the Service Offerings form, accessible to a person with the Financial Manager role.  Here, it can be defined how standard service requests and regular requests should be billed: ‘Time & Material’ or ‘Fixed Price’.  Rates can also be defined for time entries based on effort classes that are related to the service offering.

When the charge type for an activity is ‘Fixed Price’, a field becomes visible to specify the charge for that activity.  This could be the case, for example, when a standard service request, such as the restoration of a database from a backup, should always be charged at the same price.  When the charge type for an activity is ‘Time & Material’, the billing charges for the activity are calculated using the effort classes that were selected on the time entries when specialists worked on these requests.

When the timesheets for a specific month are exported, the export file now includes these charges.  In a previous release, the Billing Id, Charge ID and Activity ID had already been added to this export for billing purposes.  Now, the time entries export also includes the Charge type, Charge, Charge rate, and Charge currency columns.

The next steps that will be taken to improve the Billing Integration capability are relating skill pools to effort classes for more precise effort class selection and adding the possibility to charge a monthly fee for a service offering. Then, specific reports will be added.
