# OKTA

Xurrent has an Okta Verified Provisioning (SCIM) Certification.

- [Features](index.html#features)
- [Prerequisites](index.html#prerequisites)
- [Configuration Steps](index.html#configuration-steps)
 - [Xurrent Connection Information](index.html#xurrent-connection-information)
 - [Xurrent App](index.html#open-the-xurrent-app-and-configure-api-integration)
 - [Provisioning to App](index.html#check-the-provisioning-to-app-features)
 - [Assign People to Provisioning](index.html#assign-people-to-provisioning)
 - [Push Groups](index.html#push-groups)
- [Schema Discovery](index.html#schema-discovery)
- [Troubleshooting](index.html#troubleshooting-and-tips)

## Features

The following provisioning features are supported:

- **Push New Users**: new users created through OKTA will also be created in Xurrent.
- **Push Profile Updates**: updates made to the user’s profile through OKTA will be pushed to Xurrent.
- **Push User Deactivation**: deactivating the user or disabling the user’s access to the application through OKTA will deactivate the user in Xurrent.

> Remark: deactivating a user in Xurrent means the user will not be able to access Xurrent anymore and the user cannot be selected anymore in the service desk console by a service desk analyst. But be aware that all the user’s data will still be kept in Xurrent. When a user with the same email address is activated in Okta, the same Xurrent user record will be activated again with the link to the existing tickets.

- **Push Groups**: group memberships can be pushed to Xurrent.

> Remark: groups, for which you want the membership to be pushed from Okta to Xurrent, need to be predefined as a Xurrent organization.

## Prerequisites

Before you configure provisioning for Xurrent, make sure you have configured the General Settings and any Sign-On Options for the Xurrent app.
Make sure the ‘Application username format’ is defined as ‘Email’.

## Configuration Steps

Configure your Provisioning settings for Xurrent as follows:

### Xurrent Connection Information

Get the Xurrent SCIM endpoint and Xurrent SCIM bearer token via these instructions: [Xurrent connection information](../connection.html#xurrent-connection-information).

> Remark: you need to be the account owner of the Xurrent account to access these data. If you are not the account owner, ask the account owner for this info.

### Open the Xurrent App and Configure API Integration

- Go to the Provisioning Section
- Click on the ‘Configure API Integration’ button

- Check the ‘Enable API integration’ box
- Fill in the Base URL (your Xurrent SCIM endpoint)
- Fill in the OAuth Bearer Token (your Xurrent SCIM bearer token)

- Test the API credentials
- Save the configuration

### Check the Provisioning to App features

- Go to the Provisioning Section Settings: To app.
- Make sure the following features are enabled: ‘Create Users’, ‘Update User Attributes’ and ‘Deactivate Users’.

### Assign People to Provisioning

You need to assign the people that need to be provisioned to the Xurrent app. You have the choice to assign individual people records or to assign people based on their group membership.

For people assignments, select ‘People’, search for the people records and Assign them to the App.

For assignment via Group membership, select ‘Groups’ and search for group records.

When you select a group for provisioning, you are able to define default values for the people attributes like Preferred Language, Time Zone and Cost center.

> Remark: when you set User type on VIP, the Xurrent user will have the VIP flag set.

### Push Groups

Make sure the right Okta Groups are pushed now to Xurrent. Goto the ‘Push Groups’ tab, search for the Groups you want to push to Xurrent and add the Groups to the list.

## Schema Discovery

A detailed description of the SCIM Schemas API can be found on the [Xurrent developer site](../schemas.html).

## Troubleshooting and Tips

The OKTA users and groups that are provisioned to SCIM, can be found in the Xurrent account via the Settings console.
For each SCIM user and SCIM group that has been provisioned a record is to be found in these lists.
You can sort the list on the ‘Provisioned At’ and ‘Updated At’ timestamps. Check for any errors.

Once the SCIM records are created in Xurrent, they are processed by an automation rule that will update or create the Xurrent person records.
These automation rules implement another layer that you can use to make a correct mapping from OKTA person attributes to Xurrent person attributes.
Click on the Automation Rule execution to check the results of the execution. Click on the Actions button in the header bar to modify the Automation Rules.
