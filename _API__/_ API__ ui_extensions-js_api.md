# UI Extension Javascript API

To interact with the standard form fields from the Javascript of a UI extension, Xurrent offers the UI Extension Javascript API.

All API calls start with `ITRP`. For example, the API call `ITRP.field('note').val();` can be used to get the current value of the Note field of the Request form.

- [Get initial values](../js_api.html#get-initial-values)
- [Distinguish new and existing records](../js_api.html#distinguish-new-and-existing-records)
- [Distinguish Self Service and Specialist view](../js_api.html#distinguish-self-service-and-specialist-view)
- [Interact with form fields in Self Service](../js_api.html#interact-with-form-fields-in-self-service)
- [Interact with form fields in the Specialist view](../js_api.html#interact-with-form-fields-in-the-specialist-view)
- [Functions](../js_api.html#functions)
- [Access attributes of selected items in suggest fields](../js_api.html#access-attributes-of-selected-items-in-suggest-fields)
- [Access attributes of selected items via metadata fields of custom views](../js_api.html#access-attributes-of-selected-items-via-metadata-fields-of-custom-views)
- [Populate suggest fields](../js_api.html#populate-suggest-fields)
- [Other properties of the ITRP object](../js_api.html#other-properties-of-the-itrp-object)

## Get initial values

It is possible to get the *initial* values of a record when it is opened in edit mode. For example, to make the Attachment field required when a request is edited that has the status Assigned, use the following:

```
JavaScript
```

```
if (ITRP.record.initialValues.get('status') === 'assigned') {
 ITRP.field('attachment').required();
}
```

The general form of this API call is `ITRP.record.initialValues.get('field')`. The fields that are available depend on the type of the record that the UI extension is linked to, and are the same as those listed in the **Collection Fields** section of the respective API:

- [Requests](../../requests.html)
- [Knowledge Articles](../../knowledge_articles.html)
- [Problems](../../problems.html)
- [Workflows](../../workflows.html)
- [Tasks](../../tasks.html)
- [Projects](../../projects/index.html)
- [Project Tasks](../../project_tasks.html)
- [Configuration Items](../../configuration_items/index.html)
- [Contracts](../../contracts/index.html)
- [Organizations](../../organizations.html)
- [Sites](../../sites.html)
- [People](../../people.html)
- [Risks](../../risks.html)

Note: some of the fields are [references](../../general/data_types.html#references), such as the team to which a Request is assigned. You can access the reference attributes (usually `id` and `name` / `subject`) by passing both the name of the reference and the name of the attribute to the API, for example: `ITRP.record.initialValues.get('team', 'name')`.

## Distinguish new and existing records

To find out whether the user is adding a new record, use the following:

```
JavaScript
```

```
// Possible values: true and false
var new_record = ITRP.record.new;
if (new_record) { /* ... */ }
```

## Distinguish Self Service and Specialist view

To find out whether the user is using Self Service or the Specialist view, use the following:

```
JavaScript
```

```
// Possible values: 'self_service' and 'full_ui'
if (ITRP.context === 'self_service') { /* ... */ }
```

A practical example of this can be found in [Advanced UI Extension Examples](../advanced_examples.html#hide-field-on-creation-of-a-request-in-self-service).

## Interact with form fields in Self Service

The Javascript API offers various functions to interact with the built-in form fields of Xurrent records. For each type of record and each field, the available functions are listed below. Refer to [Functions](../js_api.html#function) for descriptions and brief examples of these functions.

### Requests

- Subject: `ITRP.field('subject')` - `required` `show` `hide` `toggle` `val`
- Note: `ITRP.field('note')` - `required` `show` `hide` `toggle` `val` `placeholder`
- Attachments: `ITRP.field('attachment')` - `required` `show` `hide` `toggle` `size`
- Asset: `ITRP.field('asset')` - `required` `show` `hide` `toggle` `val`
- Service instance: `ITRP.field('service_instance')` - `val` (read only) `on` `off` `data`
- Impact: `ITRP.field('impact')` - `val` (read only)
- Status: `ITRP.field('status')` - `val` (read only)

Note that the fields `Subject` and `Asset` can only be interacted with when the user is registering a *new* request.

The field `Asset` can only be interacted with when the user is registering a request based on a template
with the option `Asset selection in Self Service` enabled.

### Tasks

- Attachments: `ITRP.field('attachment')` - `required` `show` `hide` `toggle` `size`
- Status: `ITRP.field('status')` - `val` `on` `off` `trigger`

### Project Tasks

- Attachments: `ITRP.field('attachment')` - `required` `show` `hide` `toggle` `size`
- Status: `ITRP.field('status')` - `val` `on` `off` `trigger`

## Interact with form fields in the Specialist view

The Javascript API offers various functions to interact with the form fields of records that are available in the Specialist view. For each type of record and each field, the available functions are listed below. Refer to [Functions](../js_api.html#functions) for descriptions and brief examples of these functions.

### Requests

- Subject: `ITRP.field('subject')` - `val`
- Note: `ITRP.field('note')` - `val` `placeholder`
- Attachments: `ITRP.field('attachment')` - `required` `show` `hide` `toggle` `size`
- Internal note: `ITRP.field('internal_note')` - `val`
- Internal attachments: `ITRP.field('internal_attachment')` - `required` `show` `hide` `toggle` `size`
- Configuration items: `ITRP.field('asset')` - `required`
- Impact: `ITRP.field('impact')` - `val` `on` `off` `trigger`
- Status: `ITRP.field('status')` - `val` `on` `off` `trigger`
- Service instance: `ITRP.field('service_instance')` - `val` (read only) `on` `off` `data`

### Tasks

- Attachments: `ITRP.field('attachment')` - `required` `show` `hide` `toggle` `size`
- Impact: `ITRP.field('impact')` - `val` `on` `off` `trigger`
- Status: `ITRP.field('status')` - `val` `on` `off` `trigger`
- Configuration items: `ITRP.field('asset')` - `required`

### Project Tasks

- Attachments: `ITRP.field('attachment')` - `required` `show` `hide` `toggle` `size`
- Status: `ITRP.field('status')` - `val` `on` `off` `trigger`

### Problems

- Attachments: `ITRP.field('attachment')` - `required` `show` `hide` `toggle` `size`
- Impact: `ITRP.field('impact')` - `val` `on` `off` `trigger`
- Status: `ITRP.field('status')` - `val` `on` `off` `trigger`
- Configuration items: `ITRP.field('asset')` - `required`

### Configuration Items

- Status: `ITRP.field('status')` - `val` `on` `off` `trigger`
- System ID: `ITRP.field('systemID')` - `val` `required` `on` `off` `trigger`
- Service: `ITRP.field('service')` - `required`
- Site: `ITRP.field('site')` - `val` `required` `on` `off` `trigger`
- Location: `ITRP.field('location')` - `val` `required` `on` `off` `trigger`
- Remarks: `ITRP.field('remarks')` - `val` `required` `on` `off` `trigger`
- Attachments: `ITRP.field('attachments')` - `required`
- Nr. of processors: `ITRP.field('nr_of_processors')` - `val` `required` `on` `off` `trigger`
- Nr. of cores: `ITRP.field('nr_of_cores')` - `val` `required` `on` `off` `trigger`
- Nr. of licenses: `ITRP.field('nr_of_licenses')` - `val` `required` `on` `off` `trigger`
- Service instances: `ITRP.field('service_instances')` - `required`
- Users: `ITRP.field('users')` - `required`
- Product: `ITRP.field('product')` - `val` `on` `off` `trigger`
- RAM amount: `ITRP.field('ram_amount')` - `val` `required` `on` `off` `trigger`
- Rule set: `ITRP.field('rule_set')` - `val` (read only)
- Configuration items: `ITRP.field('ci_relations')` - `required`
- Contracts: `ITRP.field('contracts')` - `required`
- Supplier: `ITRP.field('supplier')` - `val` `required` `on` `off` `trigger`
- Serial number: `ITRP.field('serial_nr')` - `val` `required` `on` `off` `trigger`
- Financial owner: `ITRP.field('financial_owner')` - `val` `required` `on` `off` `trigger`
- PO number: `ITRP.field('po_nr')` - `val` `required` `on` `off` `trigger`
- Asset ID: `ITRP.field('assetID')` - `val` `required` `on` `off` `trigger`
- Depreciation method: `ITRP.field('depreciation_method')` - `val` `required` `on` `off` `trigger`
- In use since: `ITRP.field('in_use_since')` - `val` `required` `on` `off` `trigger`
- Warranty expiry date: `ITRP.field('warranty_expiry_date')` - `val` `required` `on` `off` `trigger`

### Risks

- Status: `ITRP.field('status')` - `val` `on` `off` `trigger`
- Mitigation target: `ITRP.field('mitigation_target_at')` - `val` `required` `readonly` `show` `hide` `toggle` `on` `off` `trigger`
- Severity: `ITRP.field('severity')` - `val` `required` `readonly` `show` `hide` `toggle` `on` `off` `trigger`
- Closure reason: `ITRP.field('closure_reason')` - `val` `on` `off` `trigger`

### Knowledge articles

- Status: `ITRP.field('status')` - `val` `on` `off` `trigger`

## Functions

### `required`

Use this function to make a field optional or required.

```
JavaScript
```

```
ITRP.field('note').required(); // Make the Note field required
ITRP.field('note').required(true); // Make the Note field required
ITRP.field('note').required(false); // Make the Note field optional
```

### `readonly`

Use this function to make a field readonly or read/write.

```
JavaScript
```

```
ITRP.field('severity').readonly(); // Make the Severity field readonly
ITRP.field('severity').readonly(true); // Make the Severity field readonly
ITRP.field('severity').readonly(false); // Make the Severity field read/write
```

### `val`

Use this function to get or set the value of a field.

```
JavaScript
```

```
// Get the value of the Subject field:
var value = ITRP.field('subject').val();

// Set the value of the Subject field to 'New subject':
ITRP.field('subject').val('New subject');

// Clear the value of the Subject field:
ITRP.field('subject').val('');

// Fill a rich text field with HTML:
ITRP.field('note').val({ html: 'This is <b>bold</b> text.' });
```

### `data`

Use this function to get additional attributes of a field.

```
JavaScript
```

```
var si_details = ITRP.field('service_instance').data('item');
var si_id = si_details.id; // ID of service instance, same as: ITRP.field('service_instance').val()
var si_name = si_details.name; // Name of service instance
var service_id = si_details.service.id; // ID of service related to service instance
var service_name = si_details.service.name; // Name of service related to service instance
```

### `show`

Use this function to make a hidden field visible.

```
JavaScript
```

```
ITRP.field('note').show(); // Show the note field
```

### `hide`

Use this function to hide a field.

```
JavaScript
```

```
ITRP.field('note').hide(); // Hide the note field
```

### `toggle`

Use this function to toggle the visibility of a field.

```
JavaScript
```

```
ITRP.field('note').toggle(true); // Show the note field
ITRP.field('note').toggle(false); // Hide the note field
```

### `size`

Use this function to get the number of attached files.

```
JavaScript
```

```
var size = ITRP.field('attachment').size();
if (size < 2) { /* ... */ }
```

### `placeholder`

Use this function to set the placeholder of the note field.

```
JavaScript
```

```
ITRP.field('note').placeholder('Describe your request here…');
```

### `on`

Use this function to attach an event handler to a field. It is based on the [jQuery on()](https://api.jquery.com/on/) function and takes two required parameters:

- `event type`: the type of event that should be handled, such as `change`, `click`, or `focus`.
- `handler function`: the function that should be called when events of the given event type occur.

```
JavaScript
```

```
// Make the Remarks field required
// when the Status is changed to 'In Production'
ITRP.field('status').on('change', function() {
 var status = ITRP.field('status').val();
 ITRP.field('remarks').required(status === 'in_production');
});
```

### `off`

Use this function to *remove* an event handler from a field. It is based on the [jQuery off()](https://api.jquery.com/off/) function and takes two required parameters:

- `event type`: the type of event that should no longer be handled, such as `change`.
- `handler function`: the handler function that was previously attached via the `on` function. Note that this should be the *same* function.

```
JavaScript
```

```
var set_remarks_value = function() {
 if (ITRP.field('status').val() === 'being_repaired') {
 ITRP.field('remarks').val('Describe what needs to be repaired:');
 // Make sure that the value of the remarks field is only filled in
 // the first time the status is set to 'Being Repaired':
 ITRP.field('status').off('change', set_remarks_value);
 }
};

ITRP.field('status').on('change', set_remarks_value);
```

### `trigger`

Use this function to manually trigger an event. It is based on the [jQuery trigger()](https://api.jquery.com/trigger/) function and takes one parameter:

- `event type`: the type of event that should be triggered, such as `change`.

```
JavaScript
```

```
// Do something when the user changes the status field to another value:
ITRP.field('status').on('change', function() { /* do something ... */ });

// Make sure that the action defined above is also performed
// when the form is initially displayed:
ITRP.field('status').trigger('change');

// The two statements above can also be combined, as follows.
// This is a common pattern when attaching an event handler.
ITRP.field('status').on('change', function() {
 /* do something ... */
}).trigger('change');
```

## Access attributes of selected items in suggest fields

When a custom field is a suggest field (for example a `organization-suggest` or a `custom-suggest`), calling `.val()` on the field returns the ID of the selected item. You may need something else to happen depending on the selected item. For example: another field should be shown only when a certain item was selected, as described in the [Advanced UI Extension Examples](../advanced_examples.html#show-field-when-custom-collection-element-is-selected). However, using the ID of the selected item in Javascript may not be desirable, because it makes it more difficult to synchronize UI Extensions between the Xurrent QA and Production environment.

To help with this use case, it is possible to access some of the attributes of the selected item.

When the suggest field allows the selection of a single value, use `.data('item')` to access these attributes.

When the suggest field allows the selection of multiple values, use `.data('items')` to get an array of selected items.

The following attributes of an item are available by default:

- `id`
- `display_name`: this is the name or subject of the item as it is displayed on the screen. In some cases the `display_name` can be a combination of multiple attributes. For example, the `display_name` of a CI is a combination of the Label and Name attribute.
- `reference`: only available for record types that have a Reference field, such as custom collection elements.

```
JavaScript
```

```
if ($color.data('item').reference === 'orange') { /* do something ... */ }

var is_orange = function(item) { return item.reference === 'orange'; };
if ($colors.data('items').filter(is_orange).length > 0) { /* do something ... */ }
```

## Access attributes of selected items via metadata fields of custom views

In addition to the standard attributes listed in the previous section, `custom-suggest` fields can expose additional attributes of items
by adding these attributes to the ‘Metadata fields’ field of the [Custom View](https://help.xurrent.com/help/custom_view/),
that the `custom-suggest` is based on.

For example, suppose you have created a custom view on [Configuration Items](../../configuration_items/index.html)
and added the field `assetID` and two custom fields called `Battery Level` and `Cost Center` to its Metadata fields.
The custom field `Cost Center` refers to a custom collection element.

These metadata fields can then be accessed in the same way as the standard attributes described in the previous section:

```
JavaScript
```

```
var assetID = $my_ci.data('item').assetID;
var assetIDs = $my_cis.data('items').map(function(item) { return item.assetID; });

var batteryLevel = $my_ci.data('item').custom_fields['Battery Level'];
var batteryLevels = $my_cis.data('items').map(function(item) { return item.custom_fields['Battery Level']; });

var costCenter = $my_ci.data('item').custom_fields['Cost Center'];
var costCenterId = costCenter.id;
var costCenterName = costCenter.display_name;
var costCenterReference = costCenter.reference;
```

A practical example is included in the [Advanced UI Extension Examples](../advanced_examples.html#access-metadata-when-item-is-selected).

**Warning**: Be careful when exposing metadata fields containing sensitive information.
Suppose a `custom-suggest` is included as a public custom field in a request template offered to end users.
These end users will then be able to obtain the metadata fields of all possible values of the `custom-suggest`.

#### Data types

The representation of the exposed data depends on the data type of the metadata field.

- Dates and timestamps: [ISO8601](https://www.w3.org/TR/NOTE-datetime) representation of the date(and/or time)
 in the UTC time zone, e.g. `2022-03-22T12:22:53Z`.
 Examples: the `created_at` and `in_use_since` fields of [Configuration Items](../../configuration_items/index.html).
- [Enumerations](../../general/enumerations/index.html): the `id` of the enumerated value, e.g. `undergoing_maintenance`.
 Examples: the `status` and `rule_set` fields of [Configuration Items](../../configuration_items/index.html).
- Booleans: as-is (i.e. `true` or `false`).
 Examples: the `site_license` and `temporary_license` fields of [Configuration Items](../../configuration_items/index.html).
- Numerical values (integer / decimal): as-is.
 Examples: the `rate` and `salvage_value` fields of [Products](../../products.html).
- Strings: as-is.
 Examples: the `name`, `label` and `assetID` fields of [Configuration Items](../../configuration_items/index.html).
- References to a record: a hash containing `id` and `display_name`, e.g. `{ id: 16, display_name: 'End-User Support, Houston' }`.
 Also includes `reference` for record types that have a Reference field, such as custom collection elements.
 Examples: the `product` and `support_team` fields of [Configuration Items](../../configuration_items/index.html).

## Populate suggest fields

As explained in the previous paragraph, when a custom field is a suggest field
(for example a `organization-suggest` or a `custom-suggest`),
calling `.val()` on the field returns the ID of the selected item.
To *populate* a suggest field with a value, you can also use the `.val()` function.
The examples below illustrate how this works.

```
JavaScript
```

```
// Set the value of a suggest field based on the ID of a record:
// ('123456' is the ID of a person record in Xurrent)
$level_1_approver.val(123456);

// Set the value of a suggest field that allows multiple values:
$level_2_approvers.val([123456, 987654]);

// When the suggest field is a custom-suggest
// based on custom collection elements,
// you can also use the reference of the custom collection element:
$cost_center.val({ reference: "cost-center-a" });

// And if the custom-suggest allows multiple values:
$cost_centers.val({ reference: ["cost-center-a", "cost-center-b"] });
```

## Other properties of the ITRP object

### `ITRP.$`

You can use [jQuery](https://api.jquery.com/) in the Javascript of UI Extensions. Access the jQuery API via `ITRP.$`.

Note that the Javascript of every new UI extension starts with the lines:

```
var $ = ITRP.$;
var $extension = $(this);
```

The `$extension` variable is then used to select fields of the UI extension, add event handlers, and so on:

```
$extension.find('#my_field').on('change', function() {
 ...
});
```

### `ITRP.hasFormData()` and `ITRP.clearFormData()`

The functions `ITRP.hasFormData` and `ITRP.clearFormData` are used to interact with all form elements in a given scope:

```
// hasData will be true if any form element in the $extension scope has a value
var hasData = ITRP.hasFormData($extension);
if (hasData) {
 // Do something
}
```

```
var $my_button = $extension.find('#my_button');
$my_button.on('click', function() {
 // Clears all form elements in the $extension scope.
 ITRP.clearFormData($extension);
});
```

A practical example using both of these functions is given on the [Advanced UI Extension Examples](../advanced_examples.html#add-another-set-of-fields) page.

### The `after-prefill` hook

The `after-prefill` hook can be used to execute a JavaScript function that should run *after* all form elements have been prefilled when editing a record.

When editing an existing record with custom fields, Xurrent performs a few technical steps:

1. Load the form HTML, including the HTML of the UI extension. At this point, all the UI extension form elements are present, *but still empty*.
2. Load and execute the Xurrent JavaScript.
3. Load and execute the JavaScript of the UI extension.
4. Fill the form elements of the UI extension with the custom field values.
5. Trigger the `after-prefill` hook.

The following JavaScript snippet illustrates this:

```
var $my_field = $extension.find('#my_field');

// This statement is executed in step 3
console.log("Value in step 3: " + $my_field.val());

ITRP.hooks.register('after-prefill', function() {
 // This statement is executed in step 5
 console.log("Value in step 5: " + $my_field.val());
});
```

Suppose that you are editing a request in which the custom field `my_field` has the value `Test`.
The above snippet will then output the following lines to the developer console of the browser:

```
Value in step 3:
Value in step 5: Test
```

Examples of the `after-prefill` hook can be found on the [Advanced UI Extension Examples](../advanced_examples.html) page.
