---
title: "Attachments in UI extensions and Automation"
date: "March 1, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/attachments-in-ui-extensions-and-automation"
slug: "attachments-in-ui-extensions-and-automation"
---

# Attachments in UI extensions and Automation

It is now possible to ask a user to supply an attachment, using a [custom field](https://developer.xurrent.com/v1/ui_extensions/advanced_examples/).  It is also possible to use [automation rules](https://developer.xurrent.com/v1/automation_rules/)to access these attachments and add them to a note.  To make this possible, a new [custom field type](https://help.xurrent.com/help/ui_extension_fields/) ‘Attachments’ has been created.

The `Minimum`and `Maximum`fields appear when the `Multiple values` box is ticked.  If it is not ticked, only one attachment may be uploaded.  Let us look at an example of a use case for this enhancement.

Imagine that our fictional Widget organization is bringing a new product to the market, named ‘Pastel’.  A request template is used to request the registration of the new product. The requester should include two types of documents to this request: the logos (or avatars) for the new product and the design documents.  In one of the workflow tasks, all these attachments must be added to a note field.

The Snippet that creates this UI extension would look like this:

`<div class="row vertical">
<label for="product_avatars" title="Product Logo">Product Logos</label>
<div id="product_avatars" data-type="attachment" class="required" data-multiple></div>
</div>
<div class="row vertical">
<label for="product_designs" title="Product designs">Product designs</label>
<div id="product_designs" data-type="attachment" class="required" data-multiple></div>
</div>`

The request with this UI extension (and several attachments already linked) could look like this:

In the automation rule, the attachments are retrieved from the 2 custom fields and added to a note:

This automation rule adds a note with all uploaded attachments to the ‘Register new Widget product in SAP’.

