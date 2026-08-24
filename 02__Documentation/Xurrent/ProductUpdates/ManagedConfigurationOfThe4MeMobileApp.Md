---
title: "Managed Configuration of the Xurrent Mobile App"
date: "June 12, 2024"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/managed-configuration-of-the-4me-mobile-app"
slug: "managed-configuration-of-the-4me-mobile-app"
---

# Managed Configuration of the Xurrent Mobile App

Managed configuration is the ability to configure and control applications on a mobile device
through Mobile Device Management (MDM) solutions. The Xurrent iOS app can be used to access
the Xurrent service from an iPhone or iPad and can be deployed from an MDM service using the
app that is available from the App Store (App Store ID: `com.itrp.App`). The Xurrent Android app
can be deployed from an MDM service using the app that is available from the (Managed)
Google Play Store (App identifier: `com.itrp.app`).

Without any configuration, on the first startup of the Xurrent app, the mobile device user will have to
enter the Xurrent account name (e.g. widget), pick the correct account domain (e.g. uk.Xurrent.com)
and depending on account configuration also select the correct single sign on provider (e.g.
Google SSO), before they can enter their user credentials (username and password). When
using MDM, the account name, account domain, and SSO provider can be pre-configured for the
mobile device user using two parameters: account_url and sso_reference. With these
settings configured, on the first startup of the Xurrent app, the mobile device user is directly asked for
their user credentials.

The account name and domain are pre-configured together by setting the `account_url`
parameter, such as widget.Xurrent.com or widget.uk.Xurrent.com. When the Xurrent account has
multiple SSO providers configured, the desired SSO provider can be pre-selected by setting the
`sso_reference` parameter. The correct value for this parameter can be found on the Xurrent
Settings page for the Single Sign-On configuration in the Configuration tab
