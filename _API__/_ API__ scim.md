# SCIM Provisioning

- [Introduction](../scim.html#introduction)
 - [Glossary](../scim.html#glossary)
 - [Benefits](../scim.html#benefits)
 - [Requirements](../scim.html#requirements)
- [Approach](../scim.html#approach)
- [Supported APIs](../scim.html#supported-apis)

## Introduction

System for Cross-domain Identity Management (SCIM) allows for automatic people management in your Xurrent account. Once enabled, Xurrent person records are automatically synchronized with the user records in your provisioning client.

This article provides the starting point to setup the provisioning. In case additional assistance is required feel free to contact your Xurrent implementation partner.

### Glossary

The following terms are used in the SCIM provisioning process.

SCIM
: System for Cross-domain Identity Management is an open standard protocol for automating user management. For more information about the protocol, see [SimpleCloud](http://www.simplecloud.info/).

Service Provider
: Service Provider refers to the Xurrent application. The service provider (Xurrent) receives identity information from the provisioning client and maps that information to Xurrent person records.

Provisioning Client
: Provisioning Client is the source of truth containing the user identities. The identity information may be shared with multiple service providers, like Xurrent. Examples of provisioning clients include Azure AD, Google SSO, Okta and OneLogin.

### Benefits

Traditionally user management is performed using a local directory service that acts a (single) source of truth. Business applications running in the local area network (LAN) connect to the directory service for authentication and provisioning of user identities. With the arrival of cloud-based applications and services, like Xurrent, this setup is not suitable anymore as the cloud services do not have access to the LAN.

The SCIM specification is designed to make managing user identities in cloud-based applications and services easier. Instead of implementing custom integrations to provision each cloud service, the SCIM protocol makes it possible for the provisioning client (e.g. the local directory service) to send identity information directly to the service provider (Xurrent) using a standardized communication protocol.

### Requirements

To enable SCIM provisioning the following is required:

- a provisioning client that supports the SCIM v2 protocol
- a Xurrent account, preferably a Xurrent *directory* account

Also, these actions are required from the following specific people:

- an account administrator of the Xurrent account, to share the SCIM access token and endpoint URL to the administrator of the provisioning client.
- an account administrator of the provisioning client, to configure the SCIM access token and endpoint URL and optionally to define a mapping.
- an account administrator of the Xurrent account, to update the user mapping and optionally the group mappings in Xurrent.

## Approach

Before connecting the provisioning client to Xurrent we recommend you to explore the [mapping possibilities](mapping.html) first.

Once the mapping is defined, it is time to [connect the provisioning client](connection.html) to your **QA account**. Use this account to fine-tune the mapping for your SCIM integration.

Next step is to [copy the mappings](mapping.html#copy-mappings) from your QA account to your production account.

Finally [connect the provisioning client](connection.html) to your **production account**.

From this point onwards all updates to users and groups in your provisioning client will be sent to Xurrent.

Finally we advise your to [rotate your SCIM token](connection.html#rotate-scim-token) at least once a year.

## Supported APIs

The following SCIM APIs are supported by Xurrent:

- [SCIM - Users API](users.html)
- [SCIM - Groups API](groups.html)
- [SCIM - Service Provider Config](service_provider_config/index.html)
- [SCIM - Resource Types](resource_types/index.html)
- [SCIM - Schemas](schemas.html)

Xurrent accepts both `PUT` and `PATCH` HTTP methods. When using `PUT` Xurrent will not automatically clear all fields that are not provided. To clear fields the caller must provide the fields with the appropriate empty value.
