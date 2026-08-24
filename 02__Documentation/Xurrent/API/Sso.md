# Single Sign-On

Xurrent can be configured to use an organization’s existing [identity provider](https://en.wikipedia.org/wiki/Identity_provider) (such as Microsoft Active Directory, Microsoft Azure B2C, OneLogin, the Okta Application Network, etc.) instead of Xurrent’ss own authentication mechanism to determine whether a user should be able to access Xurrent.

By using an existing identity provider, the organization’s Xurrent users (including the end-users who need to be able to use Self Service) will not require a separate password to access Xurrent.

## SSO Protocol

The following single sign-on protocols are supported:

- [SAML](saml/index.html)
- [OpenID Connect](openid_connect/index.html)

## Using the SSO Configuration of the Directory Account

Support domain accounts are able to use the single sign-on configuration of their directory account. After SSO has been enabled in a directory account, the checkbox ‘Login using SSO configuration of directory account’ becomes available.

Checking this box hides any SSO protocol specific section. The values for these fields are obtained from the directory account when this feature is in use.

## Multiple Identity Providers

When some users are sourced from a different Identity Provider Xurrent offers the possibility to add multiple SSO Configurations. By default users are redirected to the Primary SSO Configuration on login.
Aternative SSO Configurations are accessible using a special Login URL using a reference that you can define in the SSO Configuration form in case multiple SSO Configurations are defined.

## Debugging

If SSO has been enabled for a Xurrent account, but it does not appear to work, then the account owner can access Xurrent again by adding `/access/normal` to the URL of the Xurrent account. Once the owner is back in Xurrent, the System Logs section of the Settings Console can provide some useful information about why SSO is not working. Whenever there has been an authentication failure, an entry will have been added to the log with an explanation of what went wrong.

Also keep in mind that the clock of the servers of the identity provider need to be synchronized. If the clock is more that 2 seconds out of sync, the response from the identity provider will not be accepted by Xurrent.

If SAML is the protocol used, then another useful source of information is the SAML meta data.
