---
title: "Export Customized Views"
date: "June 12, 2023"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/export-customized-views"
slug: "export-customized-views"
---

# Export Customized Views

Xurrent exports are, in principle, technical exports. This means that they can be used to import the same (or adjusted) data back into Xurrent. This also means that these exports are not necessarily created for readability and, in general, cannot be customized within Xurrent. A new export mode has now been added to the existing export options within a view: an export of the current view.

When a specialist clicks the ellipsis menu to create an export for all or selected records in a view, the new export mode is now presented as the default. ‘All fields’ is now the choice for the already existing, technical export. The fields included for this export mode are described in the [Xurrent Developer Documentation](https://developer.xurrent.com/v1/export/). ‘Current view’ creates an export that depends on the choices the specialist had already made when looking at the view. This export is different in several ways:

- All and only the columns that are visible in the current view are exported. This includes customized columns.
- The headers and values are localized, which means they are in the language of the specialist. Times and dates are also corrected for time zone and formatting.
- Any ordering that was done on the view, for example by using the ordering options in a personal view, is preserved in this export.
- Values are presented as they are in the view. Durations, for example, are shown in hours and minutes (0:07) and not in seconds (720), like in the standard export.

The above example is an export of the current view to Excel, of incidents with status ‘Assigned’, ordered by impact, with customized columns, and Italian language setting.
