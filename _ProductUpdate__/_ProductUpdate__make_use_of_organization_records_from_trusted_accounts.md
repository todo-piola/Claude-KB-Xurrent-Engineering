---
title: "Make Use of Organization Records from Trusted Accounts"
date: "February 12, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/make-use-of-organization-records-from-trusted-accounts"
slug: "make-use-of-organization-records-from-trusted-accounts"
---

# Make Use of Organization Records from Trusted Accounts

When a managed service provider (MSP) has linked its Xurrent account with customers that have their own Xurrent account, they are able to relate the organization records of those customers to their SLAs, but they were not able to make use of these organization records that are registered in the Xurrent accounts of their customers.  That was a shame, because their customers already maintain the contact details of their organization in their Xurrent organization records.  It would be nice if the provider would be able to see this information.  But MSPs typically also want add some information about their customers in these organization records.  For example, they may want to specify who their primary purchasing contact is at the customer and what the unique number is by which the customer is known in the MSP’s billing system.

Conversely, customers that have linked their Xurrent account with the Xurrent accounts of their providers will want to see the contact details of these providers and may also want to add some additional information about a provider to its organization record.

To make this a seamless experience for MSPs as well as their customers, several enhancements have been released for organization records.  First, the ‘All Organizations’ view now also lists the provider organizations of active SLAs from [trusted accounts](https://help.xurrent.com/help/account_trust/), as well as the customer organizations of trusted accounts that are linked to an active SLA that is registered in the account in which the ‘All Organizations’ view is opened. The same is true for the providers and customers of each active first line support agreements ([FLSA](https://help.xurrent.com/help/first_line_support_agreement/)) that is registered in, or for, the account.

In the Xurrent demo data, for example, this means that the MSPs GigaTera and GlobalNet are now visible in the ‘All Organizations’ view of Widget Data Center:

A customer or provider organization record from a trusted account only shows the picture, name and contact details that are registered in the customer’s or provider’s Xurrent account.

But people who have the Service Level Manager or Account Administrator role can place such organization records of a trusted Xurrent account in Edit mode and add information to them that only the people who have access to their organization’s Xurrent account can see.  The fields that they can maintain are:

- Remarks, including attachments
- Financial ID
- Custom fields of the UI extension for organizations that has been activated in their Xurrent account

The Financial ID field is a new field.  It has been added to organization records to allow an identifier to be specified for each organization.  This identifier can then be used to establish integrations with financial systems.

When a service level manager or account administrator places an organization record of a trusted account in Edit mode, the Remarks field, the Financial ID field and the UI extension fields can be maintained.  The values entered in these fields will be visible only in their organization’s Xurrent account and do not overwrite the values that these fields have in the account in which the organization record is stored.

It is important to be aware of the following:

- The contact details of the organization record that is linked as the provider to a service are now visible to all customers that have an active SLA for this service.
- The contact details of the organization record that is linked as the customer to an active SLA are now visible to the SLA’s provider, even when the customer organization is registered in a separate Xurrent account.

This may all sound a bit complex, but for the people who use Xurrent it should feel completely intuitive.  There is no need to configure anything in Xurrent in order to make use of this enhancement.
