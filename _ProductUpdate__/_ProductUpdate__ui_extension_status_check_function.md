---
title: "UI Extension Status Check Function"
date: "November 25, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/ui-extension-status-check-function"
slug: "ui-extension-status-check-function"
---

# UI Extension Status Check Function

To be able to interact with the Status fields of requests, problems, tasks and project tasks from the Javascript of a UI extension, the following functions have been made available for account designers and account administrators:

`Val` – get or set the value of a field
`On` – attach an event handler to a field
`Off`– remove an event handler from a field
`Trigger` – manually trigger an event

With these functions, that are described in detail in the [Xurrent Developer documentation](https://developer.xurrent.com/v1/ui_extensions/js_api/), it is possible to test the status of a request, problem, task or project task in a UI Extension and perform an action.

As an example, imagine having defined a workflow for a desktop replacement. In the first task, a specialist must select an available laptop, with the status “In Stock”. A custom view, to be used in a UI extension, can be defined with every laptop filtered on the status “In Stock”. The HTML code might look as follows:

`<div class="row vertical">`

`<label for="laptop" title="Laptop">Laptop</label>`

`<div id="laptop" data-custom-view="laptop_in_stock"></div``>`

`</div>`

When this UI extension is linked to a task template, it is now possible to ensure that the specialist selects a laptop from the suggest list. The following script can now check the status of the task and make this field required:

`var $laptop = $extension.find('#laptop');`

`ITRP.field('status').on('change', function() {`

`var status = ITRP.field('status').val();`

`$laptop.required(status === "completed");`

`}).trigger('change');`
