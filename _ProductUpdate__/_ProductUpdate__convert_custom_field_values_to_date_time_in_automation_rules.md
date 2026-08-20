---
title: "Convert Custom Field Values to Date-Time in Automation Rules"
date: "April 13, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/convert-custom-field-values-to-date-time-in-automation-rules"
slug: "convert-custom-field-values-to-date-time-in-automation-rules"
---

# Convert Custom Field Values to Date-Time in Automation Rules

When an [automation rule](https://www.xurrent.com/product-updates/introducing-automation-rules) retrieves the value of a custom field, this value is always considered to be a string (i.e. just text).  To be able to use the values entered in custom date-time fields in calculations, the`to_date_time`operator has been introduced for automation rules.

The following example demonstrates how the`to_date_time`operator can be used to calculate and set the start date for a change task using the date and time specified by a requester in a custom field called ‘Planned arrival’.  The UI extension in this example looks as follows for the requester:

The automation rule below shows how the value in the Planned arrival field can be used to set the start date of a change task to 30 minutes before the planned arrival.  The action of the automation rule then enters the calculated value in the [Start no earlier than](https://help.xurrent.com/help/task_fields/) field of the task.

