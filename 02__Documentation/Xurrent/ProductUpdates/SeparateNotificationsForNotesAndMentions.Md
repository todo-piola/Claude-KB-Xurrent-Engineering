---
title: "Separate Notifications for Notes and Mentions"
date: "April 19, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/separate-notifications-for-notes-and-mentions"
slug: "separate-notifications-for-notes-and-mentions"
---

# Separate Notifications for Notes and Mentions

Some support organizations prefer to switch off the email templates that ensure that people receive a notification after a note has been added to a record that they are responsible for.  When these ‘Note Added’ email templates are disabled, though, the people who are mentioned in notes also do not receive a notification (not via email, not as a browser popup, and also not as a smartphone push notification).

To ensure that organizations can be more specific about the notifications that they want Xurrent to send to their people, a separate set of email templates has become available in the ‘Email Templates’ section of the Settings console.  The new email templates are:

- Person Mentioned in Note of Request
- Person Mentioned in Note of Problem
- Person Mentioned in Note of Release
- Person Mentioned in Note of Change
- Person Mentioned in Note of Task
- Person Mentioned in Note of Project
- Person Mentioned in Note of Project Task
- Person Mentioned in Note of Risk

These new email templates are used to determine whether a notification needs to be sent when someone is mentioned in a note.  When these email templates are enabled, they are used to generate email notifications for people who have been mentioned in a note, provided they specified in their [notification settings](https://www.xurrent.com/product-updates/introducing-notification-center) that they want to receive notifications by email.

Account designers and account administrators can customize and translate these email templates as needed for their organization.  It may be good to point out that people will never receive a ‘Note Added’ notification and a ‘Person Mentioned in Note’ notification for the same note.  For example, if a request is assigned to Ellen Brown and one of Ellen’s colleagues mentions her when adding a new note to the request, Ellen receives only the ‘Person Mentioned in Note’ notification.  If the email template ‘Person Mentioned in Note of Request’ is disabled, though, Ellen receives only the ‘Note Added to Request’ notification.
