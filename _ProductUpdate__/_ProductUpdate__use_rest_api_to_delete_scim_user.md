---
title: "Use REST API to Delete SCIM User"
date: "July 3, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/use-rest-api-to-delete-scim-user"
slug: "use-rest-api-to-delete-scim-user"
---

# Use REST API to Delete SCIM User

A new REST API capability has become available that allows administrators to delete [SCIM Users](https://www.xurrent.com/product-updates/introducing-support-for-scim).  Deleting a SCIM user may be necessary after the configuration of an identity provider was updated and the link between a SCIM user record in Xurrent and its corresponding record in the identity provider has become corrupted.

Deleting the affected SCIM user records in Xurrent allows them to be recreated by the SCIM integration.  This causes the person records in Xurrent to get automatically updated again with the information from the identity provider.

Most administrators will find it easier to [delete SCIM users in the user interface](https://www.xurrent.com/product-updates/delete-scim-user-records) of the Settings console, but some may prefer to automate this.

The syntax for deleting a SCIM user is offered in this CURL example:

$ curl -u “…” -H ‘X-4meAccount: widget’ -X DELETE ‘https://api.4me.com/scim/v2/Users/12345?hard=true’

More information about the SCIM Users API is available in the [Xurrent Developer documentation](https://developer.xurrent.com/v1/scim/users/).
