---
title: "Metadata Fields on Custom Views"
date: "April 21, 2023"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/metadata-fields-on-custom-views"
slug: "metadata-fields-on-custom-views"
---

# Metadata Fields on Custom Views

Sometimes, end users of the Xurrent Service need to be able to see more information of a record than they are able to out of the box. This could be the case when an end user needs to know who the manager of a person is, or on which site a person for whom a request is requested for, works. In other cases there may be a need to expose custom fields on configuration items to end users. These fields may be only exposed to specialists, though. It is now possible to define metadata fields on custom views, which are then available to use in the UI extension Javascript.

This is probably best explained with a simple example. Imagine that it is important for an organization that their end users are able to see who the manager is of a person selected from a person-suggest. Clicking the **ⓘ** icon in the suggest list opens up the Person preview, but that does not include the required information.

Instead, a custom view should be created, where the `Manager`column can be added to the newly added `Metadata fields` field.

Note that this is a multi-select field: multiple columns may be selected to be made available in a UI extension. These include all non-financial fields that are also available as customized columns of the respective view of that record, plus any available custom fields on that record type.

Next, a UI extension should be created with a `Person`and a `Manager`field, both based on the ‘People’ custom view. The `Manager`field is read-only.

When the user selects a person, the manager should then automatically be filled with the manager of the person. To accomplish this, the following JavaScript should be added to the UI extension:

`var $ = ITRP.$;
var $extension = $(this);

var $person = $extension.find('#person');
var $manager = $extension.find('#manager');
$manager.readonly(true);

$person.on('change', function() {
var manager = $person.data('item').manager;

// Set the 'Manager' field to the manager of the selected person.
$manager.val(manager != null ? manager.id : '');

// Hide the row if there is no manager
$manager.closest('.row').toggleClass('hide', manager == null);
});`

When the UI extension is available in a request template, the manager of a person is now displayed as soon as that person is selected.

Please refer to the[Xurrent Developer Documentation](https://developer.xurrent.com/v1/ui_extensions/js_api/) for more information and examples.
