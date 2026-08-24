---
title: "Customer Resolution Target Visibility in Request Views"
date: "January 15, 2025"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/customer-resolution-target-visibility-in-request-views"
slug: "customer-resolution-target-visibility-in-request-views"
---

# Customer Resolution Target Visibility in Request Views

When a request is registered, the next target for that request (based on the SLA, i.e. coverage, the service instance (SI) and the service offering) is displayed in the request header. The color of that header indicates whether the related service level agreement is still ok, about to breach, or already breached. In the example below, the SLA is about to be breached.

The service-oriented architecture of Xurrent makes it very easy to forward a request to a supporting team, by applying a child SI to the request. Looking at the header of the request, members of the newly assigned team then see the next target for _them_, which is based on another SLA with its own response and resolution targets. Let’s consider the following scenario:

A user registers an incident on the Expense Reporting service. According to the SLA, the Application Development team may have 4 hours to resolve the incident. After 3 hours, a specialist of the Application Development team decides the issue is probably with the database, and therefore applies the relevant child service instance to forward the request to this support team. If the resolution target for the Database team for this request is also 4 hours then that’s what will be shown in the request header. But after only 1 hour the original SLA for the request will already be breached.

The member of the Database team can still see the original SLA details in the Affected SLA section within the request, but this is not always immediately visible to specialists. Sometimes specialists collapse this section, or, in case a request template contains a long UI extension, this section may have fallen off the screen.

As a first step to give service owners and other specialists a better overview of the complete SLA chain, a customizable column has been added to all request views. This column, the Customer Target, shows the resolution target (not the response target) of the customer of the SLA within the same directory account.

In the example above, David Wood may think he has two hours to resolve the incident, but the SLA from the customer team (Application Development) only has 16 more minutes. By enabling specialists to add this column to the view, they can get a quick overview of all requests that seem safe to the assigned team, but are, in reality, in danger of breaching an SLA.
