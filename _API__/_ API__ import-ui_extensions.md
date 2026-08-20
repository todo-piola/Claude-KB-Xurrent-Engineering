# UI Extensions Import

UI extensions can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8)
or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded
[comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values)
or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a
UI extension import file can be found in the [Fields](index.html#fields) section.

## CSV Example

```
ID,Disabled,Name,Title,Category,Active version HTML,Active version CSS,Active version Javascript
,0,New Employee,Employee Details,request_template,"<p>...</p>","p { color: blue; }","var i = 1;"
15,0,Start and End Date Time,Duration of Extension,request_template,"<div class=""row horizontal"">
 <label for=""start"">Start</label>
 <input id=""start"" type=""text"" autocomplete=""off"" max=""end"" class=""required date-time"">
</div>",,
```

[download CSV](https://developer.xurrent.com/csv/ui_extensions.csv)

## Active and Prepared Version

It is possible to specify HTML/CSS/Javascript values for the Active version and for the Prepared version in the import file.

When the import file is processed, these values are treated as follows:

- If any of the Active version columns are filled in, and they differ from the current active version,
 then a new UI extension version with the specified values is created and activated.
- If any of the Prepared version columns are filled in, and they differ from the current prepared version,
 then these values are used to create a prepared UI Extension version, which is not activated.

## Fields

ID
: *Optional* **[integer](../../general/data_types.html)** —
 The unique ID of the UI extension.

disabled
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` —
 The Disabled box is checked when the UI extension is inactive.

name
: *Required* **[string](../../general/data_types.html) (max 190)** —
 The Name field is used to enter the name of the UI extension.

title
: *Optional* **[string](../../general/data_types.html)** —
 The Title field is used to enter the text that is to be displayed as the section header above the UI extension
 when the UI extension is presented within a form.

category
: *Required* **[enum](../../general/enumerations/index.html)** —
 The Category field is used to specify the type of record in which the UI extension can be selected.
 Valid values are listed in [UI Extensions API - Fields](../../ui_extensions.html#fields).

active version HTML
: *Optional* **[text](../../general/data_types.html) (max 64KB)** —
 The HTML code of the Active version

active version CSS
: *Optional* **[text](../../general/data_types.html) (max 64KB)** —
 The CSS stylesheet of the Active version

active version Javascript
: *Optional* **[text](../../general/data_types.html) (max 64KB)** —
 The Javascript code of the Active version

prepared version HTML
: *Optional* **[text](../../general/data_types.html) (max 64KB)** —
 The HTML code of the Prepared version

prepared version CSS
: *Optional* **[text](../../general/data_types.html) (max 64KB)** —
 The CSS stylesheet of the Prepared version

prepared version Javascript
: *Optional* **[text](../../general/data_types.html) (max 64KB)** —
 The Javascript code of the Prepared version
