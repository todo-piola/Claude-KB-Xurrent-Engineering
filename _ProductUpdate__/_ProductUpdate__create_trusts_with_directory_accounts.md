---
title: "Create Trusts with Directory Accounts"
date: "August 23, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/create-trusts-with-directory-accounts"
slug: "create-trusts-with-directory-accounts"
---

# Create Trusts with Directory Accounts

It is common for Xurrent customers to outsource the setup and maintenance of their Xurrent accounts to a [Xurrent partner organization](https://www.xurrent.com/partners).  To facilitate this, the customer can share the Account Administrator role of its Xurrent accounts with their Xurrent partner organization.  This makes it possible for the partner to assign the customer’s Account Administrator role to the Xurrent consultants who support the customer.  These Xurrent consultants can then use the Account Switcher to switch to one of the customer’s Xurrent accounts to adjust its configuration.

The big advantage for the customer is that the partner’s consultants are not counted as billable users for them.  For the consultants it is wonderful, because they do not need to log in to a customer’s Xurrent account each time they need to do some work for a customer; they can stay logged in to the Xurrent account of the partner organization and simply switch to the customer’s account.

There was, however, one limitation: It was not possible for customers to share the roles of their directory account with their Xurrent partner.  So, in order to provide a Xurrent consultant access to their directory account, a customer would need to create a person record in the directory account.  This person record would then become a billable user for the customer as soon as it was given the customer’s Directory Administrator role (or any other role of the customer’s directory account).  And the consultant would then need to log in to the customer’s directory account every time a small change needed to be made.

This limitation has now been removed.  Henceforth, customers can establish an [account trust](https://help.xurrent.com/help/account_trust/) between their directory account and the Xurrent account of their Xurrent partner organization.

It does not matter whether the partner only has one standard Xurrent account, or a directory account with multiple support domain accounts underneath it; a directory account can share its roles with any other type of account, provided that the trust has been established and the other account is on the Premium pricing plan.

When a directory account has a trust with a standard account or a support domain account of another organization, it becomes possible for the account administrators of the other organization to share their roles with the directory account.  This then allows a directory administrator to assign these roles to any person who is registered in the directory account.

An additional usability improvement that has been added is the ability for people, who have a role in their organization’s directory account, to use the Account Switcher to jump from the support domain account in which they normally work to the directory account.

