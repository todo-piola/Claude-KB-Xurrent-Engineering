---
title: "Stop SLA Clock When MSP Passes Request to Another MSP"
date: "May 11, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/stop-sla-clock-when-msp-passes-request-to-another-msp"
slug: "stop-sla-clock-when-msp-passes-request-to-another-msp"
---

# Stop SLA Clock When MSP Passes Request to Another MSP

Another advanced SLA tracking feature has been added to the unique [SIAM capabilities](https://www.xurrent.com/solutions/it-service-management) that Xurrent offers.  As with any of Xurrent’s advanced features, this one is also best explained using a simple use case.

In this use case, an enterprise (Widget Europe) has outsourced the management of its SAP environment to a managed service provider (SAPguru).  Widget Europe runs its SAP environment on an infrastructure that is managed by another MSP (Host Stack).  Widget Europe is therefore the customer of an SLA from SAPguru, as well as the customer of an SLA from Host Stack.

When one of Widget Europe’s SAP users submits a request that concerns the Enterprise Resource Planning (SAP) service, this request should be passed straight to SAPguru.  If SAPguru determines that there is something wrong with the infrastructure, Widget Europe does not want SAPguru to decline the request.  Instead, Widget Europe wants SAPguru to forward the request to Host Stack.

To make sure that SAPguru can do this, the service level manager of Widget Europe opens the SLA from Host Stack and selects the SAP environment, which is registered in the Xurrent account of SAPguru, in the ‘Coverage’ section.  This makes the infrastructure that Host Stack manages for the SAP environment a ‘child’ service instance of the SAP service instance. So rather than being at the same level as the SAP service, the infrastructure service is now hierarchically below it.

For SAPguru this means that their specialists can see the infrastructure that Host Stack manages in the Service Hierarchy Browser ([SHB](https://www.xurrent.com/blog/filter-capability-in-shb-extended)) when they start to work on an SAP request from Widget Europe.  They can drag this child service instance onto the request to pass it to Host Stack.

What’s new is that, after SAPguru has applied the service instance of Host Stack to one of Widget Europe’s SAP requests, the clock on the SLA of SAPguru is stopped.  And it remains stopped until Host Stack returns the request to SAPguru by setting its status to ‘Waiting for Customer’ or ‘Completed’.

SAPguru sees this in the request, because its status will be displayed as ‘Waiting for Customer’ for the specialists of SAPguru.  That’s because they are waiting for a representative of their customer Widget Europe (in this scenario the representative is Host Stack).

The reason why the clock needs to be stopped for SAPguru when they pass a request to Host Stack is that SAPguru should not be held accountable for Host Stack meeting its SLA targets.  After all, the customer of Host Stack is not SAPguru; it is Widget Europe.

Had SAPguru been selected in the Customer field of Host Stack’s infrastructure SLA, then Xurrent would not stop the clock when a request would be passed from SAPguru to Host Stack.  In that scenario, SAPguru would be responsible for the SAP environment including its infrastructure.

Xurrent distinguishes between these 2 scenarios by considering whether the MSP passing the request to another MSP is the customer of the SLA that allowed the request to be passed to the other MSP.

The example used to explain this new SLA tracking capability is extremely simple.  In practice, much more complex situations are encountered.  For example, an SLA can exist in the service hierarchy before the first SLA of an external service provider gets added to a request, or the application service is managed by an external provider but the infrastructure is provided by the data center organization of the customer, etc.  Regardless, Xurrent now stops the clock on a provider’s SLA when a request is passed to another MSP that the provider is not a customer of.
