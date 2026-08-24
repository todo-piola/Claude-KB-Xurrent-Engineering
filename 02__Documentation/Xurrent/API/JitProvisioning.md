# Just-in-Time End User Access Provisioning

Xurrent’s Just-in-Time (JIT) End User Access Provisioning functionality is used by
support organizations to automate the registration and maintenance of the
organization’s end users in Xurrent. This functionality essentially allows
organizations to offload this responsibility to their identity provider ([IdP](https://en.wikipedia.org/wiki/Identity_provider)).

When someone attempts to access an organization’s Xurrent account that has [Single
Sign-On](../sso.html) activated, the JIT End User Access Provisioning functionality
picks up the trusted information that the IdP provides to automatically register
a new person record for this user if this person could not be found in Xurrent. If
the person was already registered in the organization’s Xurrent account, the trusted
information from the IdP is used to update this person’s record.

JIT End User Access Provisioning is supported by the following single sign-on
protocols:

- [SAML](saml.html)
- [OpenID Connect](openid_connect.html)
