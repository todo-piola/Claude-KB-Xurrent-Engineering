---
title: "Delete SCIM User Records"
date: "January 20, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/delete-scim-user-records"
slug: "delete-scim-user-records"
---

# Delete SCIM User Records

Xurrent’s [SCIM Provisioning](https://www.xurrent.com/product-updates/introducing-support-for-scim) capabilities make it easy for organizations to automate the maintenance of their employee information in Xurrent by linking their Xurrent account with their identity provider, such as Azure AD, Google SSO, Okta, OneLogin, etc.

When the configuration of an identity provider is updated, however, the link between a SCIM user record in Xurrent and its corresponding record in the identity provider may become corrupted.  To easily recover from this, it is now possible to delete a SCIM user record in Xurrent.

Deleting a SCIM user record allows it to be recreated by the SCIM integration.  This ensures that the person record in Xurrent automatically gets updated again with the information from the identity provider.

By holding down the Shift or Ctrl key, it is possible to select multiple SCIM users in the view.  Pressing the Delete button in the toolbar causes all selected SCIM users to be deleted.
