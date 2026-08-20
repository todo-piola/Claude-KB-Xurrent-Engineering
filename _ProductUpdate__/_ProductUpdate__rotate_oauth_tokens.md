---
title: "Rotate OAuth Tokens"
date: "December 7, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/rotate-oauth-tokens"
slug: "rotate-oauth-tokens"
---

# Rotate OAuth Tokens

Support for [OAuth 2.0](https://www.xurrent.com/product-updates/introducing-oauth-2-0-support) has only just been introduced and now a new feature has been added that makes it easy to rotate OAuth tokens.  An OAuth token is generated whenever someone creates a [personal access token](https://www.xurrent.com/product-updates/introducing-personal-access-tokens), or when a new application is registered for an integration in the ‘Applications’ section of the Settings console.

To rotate the OAuth token of an application, an administrator can select the application in the ‘Applications’ section of the Settings console.

With the application in View mode, the administrator is able to press the **Add Token** button.  This causes a second OAuth token to be added.  At this point, the administrator can copy the client ID and client secret of the new token.  This is the only time the client secret will be visible, so it is important to copy it and to store it somewhere safe.

Because an application (or personal access token) can have up to two OAuth tokens, the **Add Token** button is hidden after a second token has been added.

With the new token added, a developer can update the integration between the application and Xurrent with the client ID and client secret of the new token.  Once this update has been made, the old token can be disabled.  After confirming that the integration still works, the old token can be deleted.

This completes the rotation of an application’s OAuth token.  [Specialists, designers and administrators](https://help.xurrent.com/help/roles/) can rotate the OAuth tokens of their personal access tokens in the same manner after clicking on their picture (or initials) in the toolbar, clicking on the ‘My Profile’ option in the User menu and opening the ‘Personal Access Tokens’ section.
