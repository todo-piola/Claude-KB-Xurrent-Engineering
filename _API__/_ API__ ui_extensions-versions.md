# UI Extensions - Versions API

## List versions of a UI extension

List all [versions](https://developer.xurrent.com/v1/ui_extesions/versions) of the UI extension with the given *:id*.

```
GET /ui_extensions/:id/versions
```

### Response

```
status: 200 OK
```

```
[{"id":7,"name":"Location Move","version_nr":1,"status":"active","activated_at":"2016-02-25T03:01:00-06:00","archived_at":null,"created_at":"2016-02-22T02:40:00-06:00","updated_at":"2016-03-18T19:04:06-05:00"},{"id":8,"name":"Location Move","version_nr":2,"status":"being_prepared","activated_at":null,"archived_at":null,"created_at":"2016-03-18T19:04:06-05:00","updated_at":"2016-03-18T19:04:06-05:00"}]
```

The response contains [these fields](../versions.html#collection-fields) by default.

### Collection Fields

By default the following [fields](../versions.html#fields) will appear in collections of UI extensions:

`activated_at` `archived_at` `created_at` `id` `name` `status` `updated_at` `version_nr`

Obtain a different set of [fields](../versions.html#fields) using the [?fields= parameter](../../general/field_selection/index.html#collection-of-resources).

### Sorting

By default a collection of UI extensions is sorted **ascending** by `id`.

The following [fields](../versions.html#fields) are accepted by the [?sort= parameter](../../general/ordering.html):

`id` `version_nr` `status` `created_at` `updated_at`

## Get a single version of a UI extension

```
GET /ui_extensions/:id/versions/:id
```

### Response

```
status: 200 OK
```

```
{"activated_at":null,"archived_at":null,"created_at":"2016-03-18T19:04:06-05:00","css":".row.subject {\n display: none;\n}","form_definition":null,"html":"<div class=\"row vertical\">\n <label for=\"move_from\">Move from</label>\n <input id=\"move_from\" type=\"text\" class=\"required add-to-subject\">\n</div>\n\n<div class=\"row vertical\">\n <label for=\"move_to\">Move to</label>\n <input id=\"move_to\" type=\"text\" class=\"required add-to-subject\">\n</div>","id":8,"javascript":null,"name":"Location Move","phrases":["Move from","Move to"],"status":"being_prepared","updated_at":"2016-03-18T19:04:06-05:00","version_nr":2,"compiled_css":".row.subject {\n display: none; }\n","localized_html":"<div>\n<div class=\"row vertical\"><label for=\"move_from\">Verplaats van/label><input id=\"move_from\" type=\"text\" class=\"required add-to-subject\">\n</div><div class=\"row vertical\"><label for=\"move_to\">Verplaats naar</label><input id=\"move_to\" type=\"text\" class=\"required add-to-subject\">\n</div>\n</div>","ui_extension":{"id":3,"name":"Location Move"},"formatted_activated_at":"","formatted_archived_at":"","view_audit_path":"/ui_extensions/3/versions/8/audit"}
```

The response contains [these fields](../versions.html#fields).

## Create a version in a UI extension

When a UI extension is activated using the [activate field](../../ui_extensions.html#fields), a new version with status `being_prepared` is created for that UI extension.

## Update a version of a UI extension

When the `html`, `css`, `javascript` or `form_definition` field of a UI extension is updated, the version with status `being_prepared` will be updated.

## Fields

activated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which this version of the UI extension was activated.

archived\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which this version of the UI extension was archived.

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which this version of the UI extension was created.

css
: *Readonly* **[text](../../general/data_types.html) (max 64KB)** — The CSS stylesheet.

dark\_mode\_safe
: *Readonly* **[boolean](../../general/data_types.html)** — Whether this version of the UI extension supports dark mode.

compiled\_css
: *Readonly* **[text](../../general/data_types.html) (max 64KB)** — The compiled CSS stylesheet (only available when a single version is retrieved).

form\_definition
: *Readonly* **[text](../../general/data_types.html) (max 64KB)** — The form definition used by the UI extension designer.

form\_definition\_react
: *Readonly* **[text](../../general/data_types.html) (max 64KB)** — The React component definition generated from the form definition.

html
: *Readonly* **[text](../../general/data_types.html) (max 64KB)** — The HTML code.

localized\_html
: *Readonly* **[text](../../general/data_types.html) (max 64KB)** — The HTML code with all phrases translated in the current users locale (only available when a single version is retrieved).

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of this version of the UI extension.

javascript
: *Optional* **[text](../../general/data_types.html) (max 64KB)** — The Javascript code.

name
: *Readonly* **[string](../../general/data_types.html)** — The Name of the UI extension at the time this version was created.

phrases
: *Readonly* **array** — The translatable phrases found in the HTML code.

status
: *Readonly* **[enum](../../general/enumerations/index.html)**, default: `being_prepared` — The Status field indicates the location in the life-cycle. Valid values are:
: - `being_prepared`: Being Prepared
 - `active`: Active
 - `archived`: Archived

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of this version of the UI extension. If this version of the UI extension has no updates it contains the `created_at` value.

use\_designer
: *Readonly* **[boolean](../../general/data_types.html)** — Whether this version was created using the UI extension designer.

version\_nr
: *Readonly* **[integer](../../general/data_types.html)** — The version number (1..) of this version of the UI extension.

view\_audit\_path
: *Readonly* **[text](../../general/data_types.html) (max 64KB)** — The URI to the [Audit Lines](../audit/index.html) of this version of the UI extension.
