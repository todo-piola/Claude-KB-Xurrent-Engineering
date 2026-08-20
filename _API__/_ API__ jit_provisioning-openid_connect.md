# JIT Provisioning using OpenID Connect

When using the OpenID Connect protocol, the JIT End User Access Provisioning
functionality can be activated by enabling the field ‘Allow JIT provisioning’
in the SSO configuration of the Xurrent account. Once enabled, Xurrent automatically
triggers the JIT End User Access Provisioning for each [ID
token](https://openid.net/specs/openid-connect-core-1_0.html#IDToken) response
from the OpenID Connect provider.

The JIT provisioning will follow these steps:

1. If the ‘Allow JIT provsioning’ field is not enabled for the SSO configuration
 of the Xurrent account go to step **4**, else
 if the ‘Allow JIT provisioning’ field is enabled, go to step **2**
2. If a person record with the primary email address specified in either the ID
 token or [UserInfo](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo)
 response already exists in Xurrent, update this person record with the [JIT
 attributes](../openid_connect.html#attributes) present in the ID token and UserInfo responses and
 go to step **3**, else

 if no person record matching the primary email address specified in either
 the ID token or UserInfo response exists in Xurrent, generate a new person
 record with the JIT attributes included in the ID token and UserInfo
 responses and go to step **3**.
3. Save the person record. If successful, go to step **4**, else do not provide
 access and log an authentication failure in the Authentication Log and
 include all details (i.e. the validation errors).
4. Pass the ID token response to the Xurrent SSO functionality for login.

## Attributes

The following attributes (or claims) can be included in the ID token and
UserInfo responses from the IdP to ensure that the corresponding field values
are set in the person record of the person who is requesting access to Xurrent:

- *name*
- *given\_name* ¹
- *family\_name* ¹
- *middle\_name* ¹
- *picture* ²
- *email*
- *locale*
- *zoneinfo*
- *jobTitle*
- organization ³
- site ³
- manager ⁴

**¹** in case the *name* claim is not present, the name field
in Xurrent will be set to the concatenation of the *given\_name*, *family\_name* and
*middle\_name* claims.

**²** the *picture* maps onto the avatar field in Xurrent.

**³** either the ID or the Name field value - if a match is not found the corresponding field in the person record is set to blank.

**⁴** either the ID, the Primary email field value, or the Name field value - if a match is not found the corresponding field in the person record is set to blank.

### Default Values

If an attribute is not included in the ID token or UserInfo response from the
IdP, and a person record already exists for the primary email address specified
in those responses, the corresponding field value of the existing person record
does not get updated.

Similarly, if an attribute is not included in either the ID token or UserInfo
response from the IdP, and a new person record needs to be generated using the
information in those responses, the corresponding field is left blank, with the
exception of the following fields:

- *name* - default value is the value of the *email* claim (i.e. the primary
 email of the person record that is being generated)
- *locale* - default value is the locale (or language) of the Xurrent account
- *time\_zone* - default value is the time zone of the Xurrent account
- *time\_format\_24h* - default value is the default time format of the language (e.g. `true` if locale is `en-US` and `false` if locale is `de`)
