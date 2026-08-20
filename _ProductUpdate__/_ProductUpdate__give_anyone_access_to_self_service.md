---
title: "Give Anyone Access to Self Service"
date: "February 7, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/give-anyone-access-to-self-service"
slug: "give-anyone-access-to-self-service"
---

# Give Anyone Access to Self Service

[Just-in-time (JIT) provisioning](https://www.xurrent.com/product-updates/just-in-time-end-user-access-provisioning) of user access has been supported by Xurrent for a few years already.  Xurrent’s advanced [single sign-on capabilities](https://www.xurrent.com/product-updates/sso-support-for-multiple-identity-providers) have also supported [OpenID Connect](https://www.xurrent.com/product-updates/support-for-openid-connect) for a while now.  What’s new is that Xurrent allows OpenID Connect and JIT provisioning to be combined. That makes it possible to give people, who do not yet have a person record in Xurrent, access to Xurrent Self Service with their Google, LinkedIn or Microsoft account credentials.

Setting this up is pretty easy.  After creating the app or project in the identity provider, a Xurrent account owner can go to the ‘Single Sign-on’ section of the Settings console.  There it is possible to add another single sign-on configuration for the identity provider, for example for Google.

The result is that people are able to access the organization’s self-service portal with their Google account.  If they are already logged into their Google account, they will be given access to Xurrent, even if they do not have a person record in Xurrent yet.  That’s because Xurrent’s JIT provisioning ensures that, before providing access, the information from a person’s Google account is used to generate a new person record.  This person record gets populated with the name, email address, picture and language preference that is stored in his or her Google account.

The next time this person attempts to access Xurrent using with his or her Google account’s credentials, Xurrent will recognize that the person record already exists and provide access without creating another person record.  If the JIT attributes (or claims) included in the response from Google contain updated information, the Xurrent person record gets updated automatically.

This works not only for Google, but for any identity provider that supports the OpenID Connect protocol.  Since many governments already provide their citizens online access using an identity provider that supports OpenID Connect, it is now possible for these governments to give their subjects secure self-service access to Xurrent without having to create a person record in Xurrent for every citizen.
