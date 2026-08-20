---
title: "Reprocess Inbound Email"
date: "February 27, 2024"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/reprocess-inbound-email"
slug: "reprocess-inbound-email"
---

# Reprocess Inbound Email

Xurrent is an elaborate service management solution that enables organizations’ specialists (and end users) to easily work together via the Specialist Interface, Xurrent Self Service, or the Xurrent Mobile App. This should, in principle, make the use of email all but obsolete. Even so, email is still a much used means of communication. The [Xurrent Mail API](https://developer.xurrent.com/v1/requests/mail/) can be used by end users and monitoring tools to submit requests by sending email to the email address of a service provider organization’s Xurrent account. Inbound emails that could not be processed can be visualized in the [‘Inbound Email’](https://www.xurrent.com/blog/inspect-inbound-email) section of the Settings console. From here, it is now possible to reprocess those emails.

Several security checks are done on inbound email, such as SPF, DKIM, and DMARC checks. Emails are also checked on viruses and spam content. If any of those checks fail, the email is not processed and ends up in the Inbound Email ‘bucket’. Upon selecting such an email, the **Ignore Checks and Reprocess** button is now shown.

Pressing this button will result in the email being processed without running these tests again, and setting the results to ‘Pass’. Caution is therefore advised. The original entry in the ‘Inbound Email’ view now has a new line: ‘Reprocessed by’. This contains a name and link to the new entry in the ‘Inbound Email’ view.

Reversely, the newly created entry in this view includes a line saying: ‘Reprocess of’, referring to the reprocessed email and showing the contents of this email.

It is also possible that an email could not have been processed for other reasons than these checks. In such cases a **Reprocess** button will be shown.
