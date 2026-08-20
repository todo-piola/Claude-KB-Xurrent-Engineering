---
title: "Only Accept Email from Specific People"
date: "March 25, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/only-accept-email-from-specific-people"
slug: "only-accept-email-from-specific-people"
---

# Only Accept Email from Specific People

Most organizations want to encourage their employees to use the self-service portal when they need some help.  That way, people will be offered knowledge articles with which they might be able to help themselves.  And if a knowledge article cannot help, they can select a request template that tells them what information is needed to get their standard request completed in the most efficient fashion.  Such organizations may want to switch off the ability to submit new requests via email.

Xurrent has already made it possible to [prevent the generation of new requests from inbound email](https://www.xurrent.com/product-updates/prevent-people-from-sending-email-to-4me).  But completely switching off the [inbound email interface](https://developer.xurrent.com/v1/requests/mail/) may not be possible for all organizations.  That’s because many have monitoring tools passing actionable events to Xurrent via email.

To accommodate this, Xurrent now makes it possible for account administrators to specify in the ‘Email Policy’ section of the Settings console that a few special people can continue to create new requests by sending email messages to the Xurrent account’s inbound mailbox, or to one of the [team’s email addresses](https://www.xurrent.com/blog/give-your-teams-an-email-address).

To make it easy to configure this, the old checkbox has been replaced by a new field called ‘Generate new requests’.  This field offers the options:

- Never
- Only From Allowed People
- Always

For new Xurrent accounts, this field is set to ‘Never’ by default.

When it is set to ‘Only From Allowed People’, though, it becomes possible to select the special person records from which email address(es) the Xurrent account should still accept email for the generation of new requests.

Administrators may also notice that the field label of the last field has been updated from ‘Whitelist’ to ‘Skip delivery checks for’.  The new label is just a little more intuitive and should not offend anyone.
