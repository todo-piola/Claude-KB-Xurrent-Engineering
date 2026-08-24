---
title: "Introducing Personal Access Tokens"
date: "June 12, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-personal-access-tokens"
slug: "introducing-personal-access-tokens"
---

# Introducing Personal Access Tokens

As announced during the Xurrent Connect 2020 event, Xurrent now makes it possible for all people who have access to the Xurrent Specialist Interface (i.e. auditors, specialists, designers and administrators) to generate personal access tokens.

To create a personal access token, people can click on their avatar or initials in the upper right corner of the browser window.  That makes it possible to select the ‘My Profile’ option.  After selecting this option, the section ‘Personal Access Tokens’ can be opened from the left side of the screen.

In this section, a new personal access token can be created by pressing the toolbar button with the big plus sign.

Personal access tokens deny all access by default.  A scope must be defined for a personal access token to allow it to use some of the [Xurrent API capabilities](https://developer.xurrent.com/).  The scope of a personal access token that will be used for the integration with a monitoring tool can, for example, be limited to the creation of new requests in a specific Xurrent account.

Regardless of the defined scopes, a personal access token can never provide more access than the roles granted to the person who created the personal access token.

A personal access token can be more secure than an API token because people have greater, more fine-grained, control over what each of their tokens is permitted to do.  Personal access tokens are also more secure because of the way they are generated and validated.  They act like OAuth tokens and have strong cryptographic characteristics.

Because of this improved security, it is recommended to stop the use [API tokens](https://www.xurrent.com/blog/securing-api-tokens) and to replace them with personal access tokens.

