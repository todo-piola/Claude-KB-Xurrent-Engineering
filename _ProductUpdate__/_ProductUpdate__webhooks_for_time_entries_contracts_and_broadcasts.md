---
title: "Webhooks for Time Entries, Contracts and Broadcasts"
date: "January 28, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/webhooks-for-time-entries-contracts-and-broadcasts"
slug: "webhooks-for-time-entries-contracts-and-broadcasts"
---

# Webhooks for Time Entries, Contracts and Broadcasts

[Xurrent’s Webhooks API](https://developer.xurrent.com/v1/webhooks/) has been extended to allow organizations to build near real-time integrations that use the time entry data in Xurrent to update their financial application.  This is especially useful for managed service providers (MSPs) that use Xurrent’s time entry data as input for the invoices they generate for their customers.

To make it possible for developers to tell when a time entry was created, updated or deleted, the following webhook events have been added:

- time_entry.create
- time_entry.update
- time_entry.delete

While the Xurrent Development team was working on the Webhooks functionality anyway, they also made the following event options available for Contracts and Broadcasts:

- contract.create
- contract.update
- broadcast.create
- broadcast.update

The first two options make it possible for organizations to trigger an integration when a contract is added or modified to keep their financial application in sync.  And the broadcast events may be popular with developers who want to display Xurrent broadcasts in their applications.

Also added was the following webhook event option:

- request.major-incident-status-changed

This makes it possible to trigger an integration script whenever the Major incident status field of a request is set or updated.
