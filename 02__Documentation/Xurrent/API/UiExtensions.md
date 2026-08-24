# UI Extensions API

- [List UI extensions](../ui_extensions.html#list-ui-extensions)
- [Get a single UI extension](../ui_extensions.html#get-a-single-ui-extension)
- [Create a UI extension](../ui_extensions.html#create-a-ui-extension)
- [Update a UI extension](../ui_extensions.html#update-a-ui-extension)
- [Fields](../ui_extensions.html#fields)

## List UI extensions

List all UI extensions for an account:

```
GET /ui_extensions
```

### Response

```
status: 200 OK
```

```
[{"id":3,"name":"Location Move","disabled":false,"created_at":"2016-03-18T19:04:06-05:00","updated_at":"2016-03-18T19:04:06-05:00","active_version":{"id":7,"name":"Location Move","version":1},"prepared_version":{"id":8,"name":"Location Move","version":2}},{"id":2,"name":"SAP Finance field option","disabled":false,"created_at":"2016-03-18T19:04:06-05:00","updated_at":"2016-03-18T19:04:06-05:00","active_version":{"id":5,"name":"SAP Finance field option","version":1},"prepared_version":{"id":6,"name":"SAP Finance field option","version":2}}]
```

The response contains [these fields](../ui_extensions.html#collection-fields) by default. [Filtering](../ui_extensions.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of UI extensions.

### Collection Fields

By default the following [fields](../ui_extensions.html#fields) will appear in collections of UI extensions:

`active_version` `created_at` `disabled` `id` `sourceID` `name` `prepared_version` `updated_at`

Obtain a different set of [fields](../ui_extensions.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../ui_extensions.html#fields):

`id` `source` `sourceID` `name` `created_at` `updated_at` `disabled`

### Sorting

By default a collection of UI extensions is sorted **ascending** by `name`.

The following [fields](../ui_extensions.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single UI extension

```
GET /ui_extensions/:id
```

### Response

```
status: 200 OK
```

```
{"active_version":{"id":7,"name":"Location Move","version":1},"category":"request_template","created_at":"2016-03-18T19:04:06-05:00","css":".row.subject {\n display: none;\n}","description":"Location move request template UI Extension","disabled":false,"html":"<div class=\"row vertical\">\n <label for=\"move_from\">Move from</label>\n <input id=\"move_from\" type=\"text\" class=\"required add-to-subject\">\n</div>\n\n<div class=\"row vertical\">\n <label for=\"move_to\">Move to</label>\n <input id=\"move_to\" type=\"text\" class=\"required add-to-subject\">\n</div>","id":3,"javascript":null,"name":"Location Move","phrases":["Move from","Move to"],"prepared_version":{"id":8,"name":"Location Move","version":2},"compiled_css":".row.subject {\n display: none; }\n","localized_html":"<div>\n<div class=\"row vertical\"><label for=\"move_from\">Verplaats van</label><input id=\"move_from\" type=\"text\" class=\"required add-to-subject\">\n</div><div class=\"row vertical\"><label for=\"move_to\">Verplaats naar</label><input id=\"move_to\" type=\"text\" class=\"required add-to-subject\">\n</div>\n</div>","title":"Information","localized_title":"Informatie","updated_at":"2016-03-18T19:04:06-05:00"}
```

The response contains [these fields](../ui_extensions.html#fields).

## Create a UI extension

```
POST /ui_extensions
```

When creating a new UI extension [these fields](../ui_extensions.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../ui_extensions.html#fields) of the created UI extension and is similar to the response in [Get a single UI extension](../ui_extensions.html#get-a-single-ui-extension)

## Update a UI extension

```
PATCH /ui_extensions/:id
```

When updating a UI extension [these fields](../ui_extensions.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../ui_extensions.html#fields) of the updated UI extension and is similar to the response in [Get a single UI extension](../ui_extensions.html#get-a-single-ui-extension)

## Fields

activate
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Set to `true` to promote the Prepared Version to the Active Version. If the was an Active Version, it will be Archived.

active\_version
: *Readonly Optional* **[reference](../general/data_types.html#references) to [UI extension Version](versions.html)** The version with Status `active`.

category
: *Required* **[enum](../general/enumerations/index.html)** — The Category field is used to select the type of record in which the UI extension can be selected. Valid values are:
: - `request_template`: Request Template
: - `knowledge_article_template`: Knowledge Article Template
 - `problem`: Problem
 - `release`: Release
 - `workflow_template`: Workflow Template
 - `task_template`: Task Template
 - `project`: Project
 - `project_task_template`: Project Task Template
 - `service`: Service
 - `service_instance`: Service Instance
 - `product`: Product
 - `product_category`: Product Category
 - `contract`: Contract
 - `organization`: Organization
 - `team`: Team
 - `person`: Person
 - `site`: Site
 - `risk`: Risk
 - `custom_collection`: Custom Collection
 - `scim_user`: SCIM User
 - `app_offering`: App Offering
 - `shop_article`: Shop Article

compiled\_css
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — The compiled CSS stylesheet of the Active Version (if available).

dark\_mode\_safe
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether the UI extension will display in dark mode. If disabled, the UI extension will always appear in light mode, even when the user has dark mode enabled.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the UI extension was created.

created\_by
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Created by field is automatically set to the person who created the UI extension.

css
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The CSS stylesheet; Shows the CSS stylesheet of the Active Version on retrieval and sets the CSS stylesheet of the Prepared Version if updated.

description
: *Optional* **[string](../general/data_types.html) (max 64KB)** — The Description field is used to enter a very short description of the ui extension.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the UI extension is inactive.

form\_definition\_json
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The JSON definition of the form for use by the UI extension designer.

hide\_note
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether the Note field is hidden on the form.

html
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The HTML code; Shows the HTML code of the Active Version on retrieval and sets the HTML code of the Prepared Version if updated.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the UI extension.

javascript
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Javascript code; Shows the Javascript code of the Active Version on retrieval and sets the Javascript code of the Prepared Version if updated.

localized\_html
: *Readonly* **[text](../general/data_types.html) (max 64KB)** — The HTML code of the Active Version with all phrases translated in the current users locale (if available).

name
: *Required* **[string](../general/data_types.html) (max 190)** — The Name field is used to enter the name of the UI extension.

phrases
: *Readonly* **array** — The translatable phrases used in the version with Status `active`.

prepared\_version
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension Version](versions.html)** The version with Status `being prepared`.

show\_on\_complete
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Whether the UI extension is shown on completion of the related record.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

title
: *Optional* **[string](../general/data_types.html)** — The Title field is used to enter the text that is to be displayed as the section header above the UI extension when the UI extension is presented within a form.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the UI extension. If the UI extension has no updates it contains the `created_at` value.

updated\_by
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Updated by field is automatically set to the person who last updated the UI extension.
