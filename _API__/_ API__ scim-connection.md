# SCIM Connection

- [Requirements](../connection.html#requirements)
- [Xurrent connection information](../connection.html#xurrent-connection-information)
- [Configure provisioning client](../connection.html#configure-provisioning-client)
 - [Azure AD](../connection.html#azure-ad)
 - [Okta](../okta/index.html)
- [Rotate SCIM token](../connection.html#rotate-scim-token)

## Requirements

Before connecting the provisioning client to Xurrent we recommend you to explore the [mapping possibilities](../mapping.html) first.

At least two people need to be involved to connect the provisioning client to Xurrent:

1. the Xurrent account owner to retrieve the [Xurrent connection information](../connection.html#xurrent-connection-information)
2. the administrator of the provisioning client to [configure the provisioning client](../connection.html#configure-provisioning-client)

We recommend that you first setup the connection for your **QA account** to fine tune the [mapping](../mapping.html).

## Xurrent connection information

Login to Xurrent as the account owner and go to the *Settings* console. Open the *Apps Store* and add the *SCIM Provisioning*, *SCIM • Azure AD*, *SCIM • Okta*, or *SCIM • OneLogin* application, once added select the *Provider* and click *Save*.

Here you will find your SCIM endpoint and the SCIM access token:

Both values need to be shared with the administrator of the provisioning client.

**Important** The SCIM access token is confidential and must be shared in a secure way.

## Configure provisioning client

The configuration on the provisioning client will be different, of course, for each provisioning client. For some provisioning clients you will find a separate section below with some additional details based on past experience of Xurrent customers with these provisioning clients.

- [Azure AD](../connection.html#azure-ad)
- [Okta](../okta/index.html)

When your provisioning client is not listed here, please take the following into consideration.

The *Endpoint* definition [states](https://tools.ietf.org/html/rfc7643#section-1.2) that the `Users` and `Groups` resources must be accessible on the following URLs:

```
https://api.xurrent.com/scim
https://api.xurrent.com/scim/v2
```

Some provisioning clients automatically append `/scim` or `/scim/v2` to the endpoint, while others don’t. The best way to test this is to first provide `https://api.xurrent.com/scim/v2` as the endpoint, then try `https://api.xurrent.com/scim` and fallback to `https://api.xurrent.com`.

The SCIM access token is a [bearer access token](https://tools.ietf.org/html/rfc6750#section-6.1.1). Most provisioning clients default to this type of access token for the SCIM integration and you can simply copy the Xurrent SCIM token directly to the provisioning client.

In case the provisioning client requires the full [HTTP Authorization header](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.8) prepend the token with `Bearer` as follows:

`Bearer 9bf7650e318d370b2447355a3d97ecaf52faa9ebb2a9e511286bb692d65fb3ad`

### Azure AD

**Tenant URL** `https://api.xurrent.com/scim/v2`

**Secret Token** `9bf7650e318d370b2447355a3d97ecaf52faa9ebb2a9e511286bb692d65fb3ad`

## Rotate SCIM token

Xurrent advises to rotate your SCIM token at least once a year. Login to Xurrent as the account owner and go to the *Settings* console. Open the *Apps* menu and click on the *SCIM* section and press the `Rotate SCIM token` button.

The old SCIM access token will stay valid for another 30 days. This should give you plenty of time to share the new access token with the administrator of the provisioning client (in a secure way).
