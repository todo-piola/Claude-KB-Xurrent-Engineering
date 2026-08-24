# OAuth 2.0

OAuth 2.0 is a protocol that lets external apps request authorization to private
details in a user’s Xurrent account without getting their password. This is
preferred over Basic Authentication because tokens can be limited to specific
types of data, and can be revoked by users at any time.

Before getting started, developers need to register their application in the
Applications console of their My Profile section. A registered OAuth application
is assigned a unique Client ID and Client Secret. The Client Secret should not
be shared.

Depending on the use case, one of the following grant types should be used:

- [Authorization Code Grant](authorization_code_grant.html)
 Allows third-party applications to access data on behalf of users in Xurrent after
 authorization of the application by these users.
- [Client Credentials Grant](client_credentials_grant.html)
 Allows third-party machine-to-machine applications to access data in Xurrent. To
 be able to use this, the grant type ‘Client credentials grant’ should be
 selected.
- [Token Exchange Grant](token_exchange_grant/index.html)
 Allows external systems holding a third-party identity token (e.g. an Azure AD
 JWT) to exchange it for a short-lived Xurrent access token tied to a resolved
 person. Implements [RFC 8693](https://tools.ietf.org/html/rfc8693).
- [Templated Tokens](templated_tokens/index.html)
 Allow third-party integrations to provide users with a URL that pre-fills the
 OAuth application creation form with a specific name, scopes, and grant type.

## Service URL

In order to successfully perform OAuth requests, the Xurrent application requires
the use of a OAuth service URL that references the instance of a specific
environment and region:

| Instance | Environment | Region |
| --- | --- | --- |
| `https://oauth.xurrent.com` | Production | Global |
| `https://oauth.au.xurrent.com` | Production | Australia |
| `https://oauth.uk.xurrent.com` | Production | United Kingdom |
| `https://oauth.ch.xurrent.com` | Production | Switzerland |
| `https://oauth.us.xurrent.com` | Production | United States |
| `https://oauth.xurrent.qa` | Quality Assurance | Global |
| `https://oauth.au.xurrent.qa` | Quality Assurance | Australia |
| `https://oauth.uk.xurrent.qa` | Quality Assurance | United Kingdom |
| `https://oauth.ch.xurrent.qa` | Quality Assurance | Switzerland |
| `https://oauth.us.xurrent.qa` | Quality Assurance | United States |
| `https://oauth.xurrent-demo.com` | Demo | Global |
