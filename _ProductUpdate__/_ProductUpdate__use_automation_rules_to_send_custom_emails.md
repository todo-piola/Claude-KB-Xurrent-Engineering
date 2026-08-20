---
title: "Use Automation Rules to Send Custom Emails"
date: "March 7, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/use-automation-rules-to-send-custom-emails"
slug: "use-automation-rules-to-send-custom-emails"
---

# Use Automation Rules to Send Custom Emails

After the recent enhancement that allows people to [send an email directly from a note in a request](https://www.xurrent.com/product-updates/send-emails-from-requests), another powerful feature for sending emails from Xurrent has now been delivered: sending emails using automation rules.  To make this possible, the new ‘Send email’ action is added to the ‘Update’ and ‘Add note’ actions of automation rules that were already available.

This new feature enables organizations to automatically send customized emails to people inside or outside the organization whenever a predefined condition is met.  The subject and body of the email can contain expressions, the body is a rich text field.  These emails can be sent to anyone that can be mentioned in the note of a request, task, or any record that can contain notes.

Consider, for example, an organization where an email is sent to an escalation manager and a service owner whenever a request is marked as urgent.  This can now be automated in the following way:

The sent email appears as a note in the record to which it is linked.  To send an email to multiple recipients, these must be specified in a single expression.  Array concatenation, as described in the previous Xurrent Development Update, may be used to select multiple recipients within one expression.

Another possible use for this new feature is for creating a basic email integration with an external supplier or 3rd party systems.
