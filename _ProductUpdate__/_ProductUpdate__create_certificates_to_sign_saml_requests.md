---
title: "Create Certificates to Sign SAML Requests"
date: "March 14, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/create-certificates-to-sign-saml-requests"
slug: "create-certificates-to-sign-saml-requests"
---

# Create Certificates to Sign SAML Requests

An extra feature has become available for organizations that use the SAML protocol to give their people [single sign-on access to Xurrent](https://developer.xurrent.com/v1/sso/).  This new feature allows them to add an extra layer of security by ensuring that Xurrent signs the SAML request that it sends to the organization’s identity provider (e.g. Azure AD, Okta, OneLogin, Google Cloud Identity, etc.) when someone from the organization attempts to open Xurrent.

Before Xurrent can sign these SAML requests, a certificate needs to be generated.  Administrators can do this in the new ‘Certificates’ section of Xurrent’s Settings console.  Creating a certificate is easy.  It only requires the administrator to select a cryptographic algorithm, a start date and an end date.

After creating a certificate, the administrator can download its X.509 certificate.  This is the certificate that an organization’s identity provider can use to verify that the public key belongs to Xurrent.

To get Xurrent to use the new certificate to sign the SAML requests that it generates, the owner of the organization’s Xurrent account goes to the ‘Single Sign-On’ section of the Settings console.  There the account owner can select (one of) the organization’s [single sign-on configuration(s)](https://www.xurrent.com/product-updates/sso-support-for-multiple-identity-providers) that uses the SAML protocol.  The certificate can then be selected in the optional Signing certificate field that has become available at the bottom of the form.

After selecting a certificate, the Signing algorithm field becomes available to allow the account owner to select an RSA signature algorithm for signing the SAML requests.

