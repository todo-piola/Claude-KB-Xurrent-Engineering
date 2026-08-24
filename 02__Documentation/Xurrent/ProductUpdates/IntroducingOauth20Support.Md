---
title: "Introducing OAuth 2.0 Support"
date: "December 5, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-oauth-2-0-support"
slug: "introducing-oauth-2-0-support"
---

# Introducing OAuth 2.0 Support

The Xurrent service now offers support for the [OAuth 2.0 Authorization Code](https://datatracker.ietf.org/doc/html/rfc6749) flow.  This flow makes it possible for developers to have their application ask a user for permission to access Xurrent on behalf of the user.

When a user grants an application permission, the application gets two temporary access tokens to make use of Xurrent’s APIs.  The access that these tokens give the application is limited to the access that the user has in Xurrent.  This access is further restricted to the scope defined by the Xurrent administrator who registered the application in Xurrent.

Administrators can register applications in Xurrent by going to the Settings console and opening the new ‘Applications’ section.  When registering an application, the scope of the application’s access to Xurrent needs to be defined.  Later, when a user gives the application access Xurrent, the application’s access to Xurrent will be limited to the access afforded by the user’s [Xurrent roles](https://help.xurrent.com/help/roles) and this access is further limited to the scope defined by the developer who registered the application in Xurrent.

After registering the application in Xurrent, the administrator has the opportunity to copy the client ID as well as the client secret.  The client secret will only be displayed this one time, so it is important to copy it and to store it somewhere safe.

With the application registered in Xurrent, a developer is now able to establish the integration between the application and Xurrent.

The authorization flow that this integration will rely on works as follows:

1. A user clicks on a login or authorization link within the third-party application.  The third-party application now needs to retrieve data that the user is allowed to access in Xurrent.

1. The third-party application redirects the user to perform an authorization request against the /oauth/authorize endpoint of Xurrent to retrieve an authorization code.  At this point, the application passes the following information to Xurrent:

- the client ID of the application record in Xurrent
- the redirect URI – this is the web address to which the user is sent after access is granted.

1. Xurrent checks if the user has previously authorized the third-party application to access Xurrent.
If authorization was already provided, the flow continues with step 5.
If not, Xurrent will show the user an authorization prompt.

1. The authorization prompt asks the user to either ‘Deny’ or ‘Allow’ the third-party application access to Xurrent.
If the user denies, the flow ends.
If the user allows access, this authorization is registered in Xurrent.

1. Xurrent generates an authorization code and returns this code to the third-party application as part of the redirect URL.

1. The third-party application performs an access token request against Xurrent’s /oauth/token endpoint to request an access token and a refresh token.  The following data is provided by the application:

- the client ID of the application record in Xurrent,
- the client secret of the application record in Xurrent,
- the authorization code the application received from Xurrent in step 5, and
- the redirect URI that was provided in step 2.

1. Xurrent then generates a temporary access token and a refresh token.
The access token allows the third-party application to retrieve data from Xurrent on behalf of the user.  An access token is valid only for 1 hour.
The refresh token allows the third-party application to retrieve a new access token and refresh token when the access token expires.  A refresh token is valid for 2 weeks.
Xurrent returns these two tokens to the third-party application.

1. The third-party application uses the tokens to make Xurrent API requests.

1. Xurrent returns API responses to the third-party application.

1. The third-party application uses the data received in the API responses to render a page for the user or perform a background action.

It is important to point out that after a user has permitted a third-party application to access Xurrent in step 4, the user is able to see this in the ‘Access & Security’ section when the user opens ‘My Profile’ in Xurrent.

This is also where users can revoke the permissions they provided to third-party applications.  When a user revokes the authorization from an application, the access tokens that the application obtained from Xurrent for the user immediately stop working.

More information about the OAuth 2.0 Authorization Code flow can be found on the Xurrent Developer website.
