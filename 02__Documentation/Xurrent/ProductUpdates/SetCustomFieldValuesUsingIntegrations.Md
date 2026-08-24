---
title: "Set Custom Field Values Using Integrations"
date: "September 13, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/set-custom-field-values-using-integrations"
slug: "set-custom-field-values-using-integrations"
---

# Set Custom Field Values Using Integrations

UI extensions can be used to add custom fields to, for example, all [problem](https://www.xurrent.com/product-updates/adding-a-ui-extension-for-problems) or [person](https://www.xurrent.com/product-updates/add-fields-to-person-site-and-contract-forms) records. But when the [SCIM automation rule](https://www.xurrent.com/product-updates/introducing-support-for-scim)s or [Xurrent’s REST API](https://developer.xurrent.com/v1/) would be used to populate the custom fields, the UI extension would not become visible until the record was manually saved or updated using the import/export functionality.

This has now been adjusted to ensure that the UI extension becomes visible as soon as a custom field value is specified in a record for which only one UI extension can be defined (e.g. for person, organization and site records).

The primary objective of this UI extension improvement is to make it easy for organizations to configure their [SCIM integration](https://developer.xurrent.com/v1/scim/) so that it automatically maintains the custom fields they defined for their person records.
