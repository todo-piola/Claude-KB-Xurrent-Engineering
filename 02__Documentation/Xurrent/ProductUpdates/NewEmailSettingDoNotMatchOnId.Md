---
title: "New Email Setting: (do not) Match on ID"
date: "May 28, 2024"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/new-email-setting-do-not-match-on-id"
slug: "new-email-setting-do-not-match-on-id"
---

# New Email Setting: (do not) Match on ID

When an[inbound email](https://developer.xurrent.com/v1/requests/mail/) is received, its content may be added as a note to an existing record. This requires that the option ‘Allow replies to be added as notes’ is checked in the Email Policy of the receiving Xurrent account and the record to which the note is added is allowed to be accessed by the sender. The record should also not be completed for longer than a configured number of days. One of the ways an inbound email was automatically related to an existing record was by recognizing a reference to its ID in the subject of the email. This can now be turned off with a setting.

The reason for such a setting is that it is not always correct to add a note to a record with an ID that was mentioned in the subject. Take this example: when a person sends the email address of an organization’s Xurrent account with the subject ‘Related issue found after resolving request 12345’, or: ‘Same laptop as in request 23456 required’, these emails should create new requests and not a note in the referred request. It turns out that in some organizations this happens quite often.

A new setting has been added to the ‘Email Policy’ section of the Settings console.

This new setting is enabled by default.
