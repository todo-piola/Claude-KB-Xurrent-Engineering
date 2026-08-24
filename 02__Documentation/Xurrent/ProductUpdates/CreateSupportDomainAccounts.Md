---
title: "Create Support Domain Accounts"
date: "April 11, 2023"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/create-support-domain-accounts"
slug: "create-support-domain-accounts"
---

# Create Support Domain Accounts

When the Xurrent service is set up and it is used by multiple support domains of the same organization, a [directory structure](https://help.xurrent.com/help/accounts/) is created with several support domain accounts.  If, at any time, it is decided that more support domain accounts should be added, this can easily be requested at the Xurrent Service Desk.  But from now on, the directory account owner is also able to do this.  A new ‘Support Domains’ section has been added to the settings console of directory accounts, only visible to the account owner.  By default, it shows a view of all enabled support domains of the directory account.

By pressing the **+** button (Add Support Domain), a new support domain can be added under the directory account. Most of the fields are already filled in with default values, taken from the directory account settings. These can be adjusted, if needed.

The account URL is always prefixed by the name of the directory account, and post-fixed by Xurrent.com.  If this is undesirable for any reason, the creation of the support domain will have to be requested via Xurrent support.  The account owner of the new support domain is automatically set to the directory account owner.  This can be adjusted from the ‘Account Settings’ section of the Settings menu of the newly created support domain account.  It is not possible to edit a support domain from the ‘Support Domains’ view.

It is however possible for directory account owners to disable support domains.  When a support domain is selected from the view, the ‘Disable Support Domain…’ option is available from the Actions menu.

After a support domain is disabled:

- Account trusts with the account are revoked
- Permissions in the account are revoked.
- Service level agreements provided to other accounts are expired.
- First level support agreements are expired.
- SSO configurations are disabled.

These actions cannot be undone.  In addition, after 24 hours, all records that can be trashed, such as requests, problems and tasks, will be added to the trash.  After 30 days, the account will be permanently removed and can no longer be re-enabled.
