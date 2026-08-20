# JIT Provisioning using SAML

When using the SAML protocol, the JIT End User Access Provisioning functionality
does not need to be activated separately. As soon as the Single Sign-On (SSO)
functionality is activated for an organization’s Xurrent account, Xurrent automatically
reviews each SAML response that it receives from the organization’s IdP to
determine if the JIT End User Access Provisioning functionality need to be
triggered.

JIT provisioning is performed if:

- the SAML response does not contain the `jit` attribute, or
- the `jit` attribute value in the SAML response contains `true`, `T` or `1`.

In addition, the SAML response must include one or more of the JIT person attributes listed in the next section.

Otherwise, if the SAML response does not contain any JIT person attributes or if the `jit` attribute contains `false`, `F` or `0`, JIT provisioning is skipped and the SAML response is passed on to the Xurrent SSO functionality for login.

The JIT provisioning algorithm works as follows:

- If a person record already exists in the Xurrent account with the primary email address specified in the SAML response, then:
 - If all JIT attributes are the same as the corresponding field
 values in the existing person record, there is no need to do anything.
 - Otherwise, Xurrent updates the person record with the JIT attributes included in the SAML response.
- Otherwise (if a person record does not yet exist), Xurrent creates a new person record with the JIT attributes included in the SAML response.

If something goes wrong when saving the new or existing person record, Xurrent does *not* provide
access and logs an authentication failure in the Authentication Log that
includes details of the SAML response attributes and the validation
errors.

If JIT provisioning completes successfully, the SAML response is passed to the Xurrent SSO functionality for login.

## Attributes

### Person Attributes

The following attributes can be included in the SAML response from the IdP to
ensure that the corresponding field values are set in the person record of the
person who is requesting access to Xurrent:

- jit ¹
- on\_create ⁵
- source
- sourceID
- name ⁴
- primary\_email ⁶
- supportID
- employeeID
- authenticationID ⁶
- vip
- job\_title
- locale
- location
- time\_zone
- time\_format\_24h
- organization ²
- site ²
- manager ³
- first\_name ⁴
- last\_name ⁴

**¹** the Just-in-Time End User Access Provisioning functionality is bypassed when this attribute’s value is `false`, `F` or `0` - it is triggered when the value is `true`, `T`, `1` or when this attribute is omitted from the SAML response.

**²** either the ID or the Name field value - if a match is not found the corresponding field in the person record is set to blank.

**³** either the ID, the Primary email field value, or the Name field value - if a match is not found the corresponding field in the person record is set to blank.

**⁴** in case the Identity Provider is not able to provide a single name value, the `first_name` and `last_name` attributes may be used. When provided the name field in Xurrent will be set to the concatenation of both attributes.

**⁵** optional attribute to indicate which JIT attribute should be used for new people and not be used to update existing people. Add the JIT attribute separated by spaces, e.g. `on_create = organization site manager`.

**⁶** The attribute is ignored on update in case the **Identifier** in the Xurrent SSO Configuration is set to this attribute, on create the attribute will be set. Note that `primary_email` is required to create new person records using JIT in case the **Identifier** in the Xurrent SSO Configuration is set to `Authentication ID`.

### Telephone Number Attributes

It is possible to include multiple telephone numbers in the SAML response from the identity provider. For each telephone number a label (e.g. `work` or `home`) needs to be specified. Multiple telephone numbers with the same label can be included in the SAML response.

- telephone:work
- telephone:mobile
- telephone:fax
- telephone:home

### Custom Attributes

When a UI extension is used to add additional fields to the Person form, these custom fields can populated by including their values in the SAML response from the identity provider. The value for a custom field (e.g. Date of birth or Start date) needs to be preceded by `custom_data:` followed by the ID that the field has in the UI extension.

- custom\_data:date\_of\_birth
- custom\_data:start\_date
- etc.

### Default Values

If an attribute is not included in the SAML response from the IdP, and a person record already exists for the primary email address specified in the SAML response, the corresponding field value of the existing person record does not get updated.

Similarly, if an attribute is not included in the SAML response from the IdP, and a new person record needs to be generated using the information in the SAML response, the corresponding field is left blank, with the exception of the following fields:

- locale - default value is the locale (or language) of the Xurrent account
- time\_zone - default value is the time zone of the Xurrent account
- time\_format\_24h - default value is the default time format of the language (e.g. `true` if locale is `en-US` and `false` if locale is `de`)

## Example XML of a SAML Response with JIT Provisioning Attributes

```
<AttributeStatement>
 <Attribute Name="jit" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">true</AttributeValue>
 </Attribute>
<AttributeStatement>
 <Attribute Name="source" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">JIT Provisioning</AttributeValue>
 </Attribute>
 <Attribute Name="sourceID" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">JOHSMI</AttributeValue>
 </Attribute>
 <Attribute Name="name" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">John Smith</AttributeValue>
 </Attribute>
 <Attribute Name="supportID" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">JOHSMI</AttributeValue>
 </Attribute>
 <Attribute Name="employeeID" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">5548871</AttributeValue>
 </Attribute>
 <Attribute Name="organization" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">Widget Data Center</AttributeValue>
 </Attribute>
 <Attribute Name="site" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">23822</AttributeValue>
 </Attribute>
 <Attribute Name="telephone:work" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">+1 (212) 369 2623</AttributeValue>
 <AttributeValue type="xs:string">+1 (212) 369 2624</AttributeValue>
 </Attribute>
 <Attribute Name="telephone:mobile" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">+1 (212) 761 5019</AttributeValue>
 </Attribute>
 <Attribute Name="custom_data:date_of_birth" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">1987-06-23</AttributeValue>
 </Attribute>
 <Attribute Name="custom_data:start_date" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
 <AttributeValue type="xs:string">2017-01-31</AttributeValue>
 </Attribute>
</AttributeStatement>
```

The above information from the SAML response is parsed by Xurrent as follows;

```
{
 "jit": "true",
 "source": "JIT Provisioning",
 "sourceID": "JOHSMI",
 "name": "John Smith",
 "supportID": "JOHSMI",
 "employeeID": "5548871",
 "organization": "Widget Data Center",
 "site": "23822",
 "telephone": {
 "work": ["+1 (212) 369 2623", "+1 (212) 369 2624"],
 "mobile": ["+1 (212) 761 5019"]
 },
 "custom_data": {
 "date_of_birth": "1987-06-23",
 "start_date": "2017-01-31"
 }
}
```
