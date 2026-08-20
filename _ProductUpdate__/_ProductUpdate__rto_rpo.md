---
title: "Recovery Time Objective (RTO) & Recovery Point Objective (RPO)"
date: "July 15, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/rto-rpo"
slug: "rto-rpo"
---

# Recovery Time Objective (RTO) & Recovery Point Objective (RPO)

When providers register their services in Xurrent, they also register at least one [service offering](https://help.xurrent.com/help/service_offering/) for each service.  Each service offering defines the targets, terms and conditions for the SLAs that will later be registered for the customers that have subscribed to a service.

A provider is also able to describe how it will respond if the service becomes unavailable due to a [disaster](https://en.wikipedia.org/wiki/Disaster_recovery).  This was done in the Continuity field of a service offering.  The ‘Backup’ section of a service offering allowed providers to specify the maximum risk of data loss, the offline backup schedule and the restore duration.

It has become clear, though, that IT service providers have a lot more information to share about the backup schedule of their services, while HR or Facility Management departments have typically ignored the ‘Backup’ section altogether.  To make sure that all types of providers feel more comfortable defining their service offerings, a few changes have been made to the Service Offering form.

Specifically, the ‘Backup’ section will no longer be available when a new service offering is being prepared.  In existing service offerings, the fields of this section disappear when they no longer contain a value.  As soon as all three fields of the ‘Backup’ section are empty, the entire ‘Backup’ section is no longer available.

Replacing the ‘Backup’ section is the new ‘Continuity’ section that is now available in all service offerings.  The Continuity field that already existed has been renamed to ‘Continuity measures’ and moved to the bottom of this section.

Above the Continuity measures field, two new fields have been added.  They are called:

- Recovery time objective – The Recovery Time Objective (RTO) is the targeted duration of time and a service level within which the service must be restored after a disruption or disaster.
- Recovery point objective – A Recovery Point Objective (RPO) is the maximum targeted period in which data might be lost from the service due to a disruption or disaster.

All providers can use the Recovery time objective field to specify how quickly they aim to have the service available again after a service disruption.  The Recovery point objective will mostly be applicable for IT services, but providers that may, for example, suffer a loss of paper documents in a disaster may also find it useful.  The Continuity measures field will be useful for all providers that want to explain how prepared they are to perform a service recovery.

The hope is that reorganizing the Service Offering form in this fashion will make it easier to compare the continuity targets of different service offerings, while at the same time providing more freedom to describe all the continuity measures.
