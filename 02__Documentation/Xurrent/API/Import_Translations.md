# Translations Import

Translations can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a
Translation import file can be found in the [Fields](index.html#fields) section.

## CSV Example

```
Locale,Type,Key,Field,Phrase,Translation
nl,product_category,297,group,Address,Adres
nl,product_category,297,name,IP Address,
nl,request_template,56,subject,Addition of Expense Reporting field option,Toevoegen van Expense Reporting veld optie
nl,request_template,56,registration_hints,"Determine on which screen and for which field the new option is required. Next, determine which additional option is required (e.g. a new expense type).
Specify these requirements in the Note field.",
nl,ui_extension,1,html.AD Username,AD Username,AD Gebruikersnaam
nl,ui_extension,1,html.Hidden text,Hidden text,Verborgen text
```

[download CSV](https://developer.xurrent.com/csv/translations.csv)

## Fields

locale
: *Required* **[string](../../general/data_types.html) (max 5)** — The locale in which the translation of the text is specified.

type
: *Required* **[string](../../general/data_types.html) (max 32)** — The type of the record from which the phrase is obtained:
: - `account_design`
 - `pdf_design`
 - `product_category`
 - `request_template`
 - `self_service_design`
 - `service`
 - `service_instance`
 - `service_category`
 - `time_allocation`
 - `ui_extension`

key
: *Required* **[decimal](../../general/data_types.html)** — The unique ID of the record from which the phrase is obtained.

field
: *Required* **[string](../../general/data_types.html) (max 70)** — The Field field is used display the label of the field from which the phrase is obtained.

phrase
: *Required* **[text](../../general/data_types.html) (max 64KB)** — The Phrase field is used display the text that is obtained from the field.

translation
: *Optional* **[text](../../general/data_types.html) (max 64KB)** — The
 Translation field is used enter the translation of the text that is displayed in
 the Phrase field. If the translation of the text is left empty, the Translation
 record (if present) will be deleted.
