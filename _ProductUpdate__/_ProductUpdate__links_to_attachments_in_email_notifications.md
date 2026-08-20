---
title: "Links to Attachments in Email Notifications"
date: "April 12, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/links-to-attachments-in-email-notifications"
slug: "links-to-attachments-in-email-notifications"
---

# Links to Attachments in Email Notifications

Many email notifications that Xurrent sends out include the last note of the record for which they are generated.  If this note includes inline images, these images are also visible in the body of the email message.  But if files are attached below the note, these files are not be included in the email notification.

Going forward, though, organizations can decide to include the links to the attachments of notes in the email notifications that are sent out from their Xurrent account.

To make use of this new feature, [account designers](https://help.xurrent.com/help/account_designer_role) and [account administrators](https://help.xurrent.com/help/account_administrator_role) can go to the ‘[Email Templates](https://help.xurrent.com/help/email/)‘ section of the Settings console, open an email template in Edit mode, place the cursor where the links to the attachments should be presented, and click on the`{{`option below the Body field to add the`note_attachments`field.

The email template could then look something like this:

Continuing with this example, let’s assume that a request has been completed with the following note:

The email notification that gets sent to the requester would then look like this (assuming no HTML formatting was added to the account’s [Email Design](https://www.xurrent.com/product-updates/beautiful-email-designs) to make the messages look nice):

The person who receives the email can use the links that point to the attachments for 1 week without requiring access to Xurrent.  If someone clicks on an attachment link that is more than 1 week old, Xurrent requires this person to authenticate before the attachment is retrieved.  In such cases, if the person is already logged in to Xurrent in the same browser, or if [single sign-on](https://developer.xurrent.com/v1/sso/) is activated, this happens automatically.  Otherwise, the person will see Xurrent’s sign-in form pop up.  After a successful login, the attachment is retrieved.

By including the attachments as links, instead of simply attaching the files to the email messages, organizations still retain some level of control over the files after the links have been sent out.  That’s because the links stop working immediately after the note with the attachments has been deleted in Xurrent.

An additional advantage is that the email messages from Xurrent do not start to take up much storage space on the mail servers and do not clog up the network when people add large attachments to notes.  Finally, when email messages are sent to the service management application of a managed service provider (MSP), this application will not reject the email messages when the size of an attachment exceeds its limit.  This last advantage is important for such email integrations, because Xurrent allows [multiple files of up to 2GB each](https://www.xurrent.com/blog/relaxed-attachment-file-size-limit) to be attached to each note, which is multiple times the file size allowed by most service management solutions.
