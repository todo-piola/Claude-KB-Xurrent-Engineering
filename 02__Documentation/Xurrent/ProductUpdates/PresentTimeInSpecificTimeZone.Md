---
title: "Present Time in Specific Time Zone"
date: "April 27, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/present-time-in-specific-time-zone"
slug: "present-time-in-specific-time-zone"
---

# Present Time in Specific Time Zone

The`to_date_time`operator recently became available to [allow automation rules to work with values entered in custom date-time fields](https://www.xurrent.com/product-updates/convert-custom-field-values-to-date-time-in-automation-rules).  Now account designers and administrators can take things a step further with the`in_time_zone(…)`function.

This new function makes it possible to retrieve a date-time value from Xurrent and convert it from UTC to another time zone.  This can be useful when a time needs to be specified in a text field.

Below is an example where a date-time value is taken from a custom field called ‘Requested delivery’.  The automation rule then writes a calculated time based on the current moment, the requested delivery, as well as the request’s completion target, to the Note field in the time zone of the requester, the time zone of the account, and the time zone in central Europe.

The result can then look as follows in the Note field of a request:

This example with 3 different time zones should probably not be used in practice, but it illustrates 3 ways to use the`in_time_zone(…)`function to dictate the time zone in which a date-time value should be expressed.
