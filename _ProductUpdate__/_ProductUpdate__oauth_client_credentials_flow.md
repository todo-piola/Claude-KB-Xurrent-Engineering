---
title: "OAuth Client Credentials Flow"
date: "December 24, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/oauth-client-credentials-flow"
slug: "oauth-client-credentials-flow"
---

# OAuth Client Credentials Flow

Xurrent’s [support for OAuth 2.0](https://www.xurrent.com/product-updates/introducing-oauth-2-0-support) has been extended to allow developers to build applications that need to interact with Xurrent, but which should not ask a Xurrent user for permission to use his or her Xurrent access rights.  Such applications may, for example, require Xurrent access to maintain records in the [CMDB](https://www.xurrent.com/features/service-configuration-and-it-asset-management), or to generate and update requests for actionable events.  These kind of machine-to-machine (M2M) interactions can now be secured using Xurrent’s support for the [OAuth 2.0 Client Credentials flow](https://datatracker.ietf.org/doc/html/rfc6749).

Administrators can find the option for this in the ‘Applications’ section of the Settings console.  There, applications can be registered that need to interact with Xurrent.  These applications were already able to make use of the [OAuth 2.0 Authorization Code](https://datatracker.ietf.org/doc/html/rfc6749) flow where humans need to grant the applications some of the access they have to Xurrent.  Now applications that do not rely on someone’s Xurrent access can also be registered.  For such applications, the new ‘Allow OAuth Client Credentials flow’ option can be checked.

When this new option is checked, the application follows the steps below to interact securely with Xurrent using the limited access rights defined for the application in Xurrent.

More information about the OAuth 2.0 Client Credentials flow can be found on the [Xurrent Developer website](https://developer.xurrent.com/v1/oauth/client_credentials_grant/).
