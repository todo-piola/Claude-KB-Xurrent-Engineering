---
title: "Create Person Records for People in CC"
date: "April 14, 2023"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/create-person-records-for-people-in-cc"
slug: "create-person-records-for-people-in-cc"
---

# Create Person Records for People in CC

An end user or a monitoring tool can submit requests by sending email to the email address of a service provider organization’s Xurrent account.  This is taken care of by the [Mail API](https://developer.xurrent.com/v1/requests/mail/). This way, [notes can also be added to an existing request](https://www.xurrent.com/product-updates/replies-to-inbound-emails-generate-notes), problem, task, etc. by including the ID of the record in the Subject field.  It is also possible to allow people who are not yet known within the system to send inbound email, if the setting ‘Register new person when email is received from unknown sender’ is enabled in the ‘Email Policy’ section of the Settings console.  For those people, person records are automatically created.

In accounts where this setting is enabled, people who are added in CC in such inbound mails are now also automatically added to Xurrent.  This enhancement makes it easier for organizations who often make use of the email functionality within requests.
