---
title: "Mitigation Target Field for Risk Management"
date: "May 14, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/mitigation-target-field-for-risk-management"
slug: "mitigation-target-field-for-risk-management"
---

# Mitigation Target Field for Risk Management

A new field has become available on the [Risk](https://www.xurrent.com/product-updates/introducing-the-risk-register) form.  It is a date field with the label ‘Mitigation target’.  This field allows organizations to prioritize their risks by setting a target date by which they intend to have mitigated each risk.

When this field is used, people will notice that the background color of a risk’s header changes when the mitigation target approaches.  The thresholds are:

- **Red** – if time to target is less than 0 minutes, else
- **Orange** – if time to target is between 0 and <240 hours, else
- **Yellow** – if time to target is between 240 and <1440 hours, else
- **Gray**

Xurrent’s [JavaScript API](https://developer.xurrent.com/v1/ui_extensions/js_api/) has been extended so that the [UI extension](https://www.xurrent.com/blog/advanced-ui-extension-examples) for risks can be used to manipulate the Mitigation target field.  The JavaScript API offers the same functions for the Mitigation target as were already available for the Severity field.

An example of how to use the JavaScript API to control the behavior of the Mitigation target field can be found in the default UI Extension for risks.  Existing customers who are using the default UI extension for risks can update the JavaScript of this UI extension by pressing the Reset button in the JavaScript tab.

The updated default JavaScript for the UI extension ensures that the Mitigation target field becomes required when the Severity field is set to ‘High’.

Setting a target for dealing with the more important risks that an organization faces is good practice.  It will also help ISO 27001 certified organizations complete their annual audit more efficiently.
