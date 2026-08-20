---
title: "Replies to Inbound Emails Generate Notes"
date: "July 12, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/replies-to-inbound-emails-generate-notes"
slug: "replies-to-inbound-emails-generate-notes"
---

# Replies to Inbound Emails Generate Notes

When an email is sent to Xurrent®, the [Mail API](https://developer.xurrent.com/v1/requests/mail/)ensures that the information in the body of the email gets added as a note in a new or existing request.  When that email was also sent to another recipient in cc, and that person decides to ‘reply to all’ from that email (and not from the email notification coming from Xurrent), a second request may unintentionally be generated.  This is no longer the case: Xurrent now detects replies to emails that generated a note or a request and adds those replies as notes to that request.

The following example shows how Grace Groupco’s reply-to-all to an inbound email from Brian Myers became a note in the same request that was generated from Brian’s email.

