---
title: "Introducing Major Incidents"
date: "November 7, 2019"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-major-incidents"
slug: "introducing-major-incidents"
---

# Introducing Major Incidents

Most support organizations have a major incident management process that requires them to perform additional activities for incidents that they consider ‘major’.  This was one of the many topics discussed during this year’s [CAB meeting](https://www.xurrent.com/blog/impressions-from-4me-cab-2019).  Customers indicated that there is a need to be able to mark requests as major incidents.  That would allow them to trigger automation rules that guide them through their major incident management process.

To accommodate this, Xurrent now allows every specialist to let their organization’s major incident managers know that a top-impact incident should probably be treated as a major incident.  Specialists can click on the **Actions** button in the toolbar and select the option ‘Propose as Major Incident’ from the menu.  This option is available only if the impact of the request is ‘Top – Service Down for Several Users’ and at least one major incident manager has been selected in the organization’s first line support agreement (more about this later).

Selecting the ‘Propose as Major Incident’ option causes a dialog to pop up that gives the specialist the ability to enter a note.  By default, this will be an internal note.  The note field is not required.  Because the Note field is not required, the specialist, who is probably under a lot of pressure when there is a major incident, does not need to spend any time formulating a proper message for the major incident managers.

Notice that the name of the Xurrent account in which the request will become a proposed major incident is specified in the header above the Note field.  That is also the account which specialists will be able to see the internal note if one is added.

Once a request has been proposed as a major incident, the major incident icon is displayed in orange over the request icon.

The Major incident status field is now visible in the request.  A system note is automatically added to indicated who proposed that the request should be treated as a major incident.  This system note is also internal, which means that it is visible only for the specialists of the account for which the request is now a proposed major incident.

Setting the major incident status to ‘Proposed’ also causes Xurrent to notify all of the support organization’s major incident managers.  They receive an email that is based on the new email template ‘Major Incident Status Changed’, a notification in their Xurrent Notification Center, a browser popup, and a push notification on their smartphone if they have the Xurrent App installed.  They receive these notifications even when they have selected ‘Never’ in their ‘Notification Settings’ for email and popup notifications.

These notifications are sent each time the major incident status is updated.  After receiving the initial notification, each major incident manager can reject the proposal by updating the major incident status to ‘Rejected’.  Alternatively, a major incident manager may decide to update the major incident status from ‘Proposed’ to ‘Accepted’ to make the request an actual major incident.  This causes the color of the major incident icon to change from orange to red.

The major incident status options are:

- Proposed
- Rejected
- Accepted
- Resolved
- Canceled

The service level managers of a support organization can define who the major incident managers are in the first line support agreement (FLSA) that covers their organization’s Xurrent account. If no one is linked to the FLSA as a major incident manager, the Actions menu option ‘Propose as Major Incident’ will not be available for the organization’s specialist.

To ensure that the steps of the support organization’s major incident management process are followed, it is possible to define automation rules that are triggered by major incident status updates.

Many more [automation rules](https://help.xurrent.com/help/automation_rule_examples/) will probably be needed, for example, to ensure that the affected user community receives an update every 30 minutes, or to remind the problem manager of the service to conduct a root cause analysis after the major incident status has been set to ‘Resolved’.

To ensure that major incidents get the attention they deserve, they are always presented at the top of the Inbox views:

If the inbox view also contains some items that are [marked as urgent](https://www.xurrent.com/product-updates/mark-as-urgent), then the major incidents are still considered more urgent.  The items that are marked as urgent are therefore presented just below the requests that have the major incident status ‘Proposed’ or ‘Accepted’.
