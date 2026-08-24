---
title: "Introducing SLA Target Breach Notifications"
date: "December 6, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-sla-target-breach-notifications"
slug: "introducing-sla-target-breach-notifications"
---

# Introducing SLA Target Breach Notifications

Xurrent informs users about impending (and active) target breaches using [color codes](https://www.xurrent.com/blog/adding-a-little-color), both in the Target column of the views and in the record headers.  But sometimes, especially in the case of resolution targets for incidents, it can be desirable to inform certain people when a target is about to be breached, so that everything can be done to prevent this from happening.  To achieve this, it is now possible to configure different notifications to different people at different moments between incident registration and resolution.

First, one or more notification schemes must be set up in the new ‘SLA Notification Schemes’ section of the Settings console.  This must be done by a person who has the Service Level Manager or Account Administrator role.

For each scheme, up to three rules can be configured.  The Threshold percentage defines when a notification is sent.  This is based on the resolution target as defined in the service offering, which shall be related to this scheme in the next step.  For example: if for an incident with a resolution target of 8 hours a notification is configured with a threshold percentage of 25%, it is sent 2 hours after its registration.

Up to 6 different people can be selected for a notification.  When ‘Current assignee’ is checked and the request is not assigned to a member, it is sent to the coordinator of the team, or, if the team has no coordinator, to all team members.  These notifications are only sent when the request is assigned to the first line team or support team of the affected SLA to which this SLA notification scheme applies.

If a second (and perhaps a third) notification should be sent for this scheme, these can be configured after pressing the green Add Notification Rule button.  This way, a scheme can be created to send notifications at 25%, 50%, and 75%, for example.

Now, all that has to be done to start sending notifications for requests with an [affected SLA](https://help.xurrent.com/help/affected_sla/) that is on its way to possibly be breached, is applying an SLA notification scheme to the respective resolution targets in the relevant service offerings.  For this, the Notification scheme field is added to the ‘Response and Resolution Targets’ section for the incidents with impact ‘Low’, ‘Medium’, ‘High’, and ‘Top’.

The SLA target breach notifications are sent using the newly added email template ‘Upcoming Resolution Target for Affected SLA of Request’, which can be customized and translated in the ‘Email Templates’ section of the Settings console.
