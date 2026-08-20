# Timesheets API

- [List timesheets](index.html#list-timesheets)
- [List incomplete timesheets](index.html#list-incomplete-timesheets)
- [Get a single timesheet](index.html#get-a-single-timesheet)
- [Get day totals](index.html#get-day-totals)
- [Lock dates](index.html#lock-dates)
- [Unlock dates](index.html#unlock-dates)
- [Fields](index.html#fields)

## List timesheets

List all timesheets for an account:

```
GET /timesheets
```

The parameter `organization_id` is required to ensure that the timesheets of a specific organization are retrieved. In addition, the parameter `month_of` is required. This parameter is used to specify the month for which the timesheets are to be retrieved. A month can be selected by specifying any date of that month using the syntax `yyyy-mm-dd`.

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X GET \
 "https://api.xurrent.com/v1/timesheets?organization_id=44&month_of=2016-02-15"
```

Note that the account of a timesheet is the account of the organization to which the person of the timesheet was linked when the timesheet was generated.
The following people have access to a timesheet:

- the person of the timesheet
- the manager or substitute of the organization to which the timesheet belongs
- any person with the Auditor role (or the Directory Auditor role in case of a directory account) of the account in which the timesheet’s organization is registered
- any person with the Account Administrator role (or the Directory Administrator role in case of a directory account) of the account in which the timesheet’s organization is registered

### Response

```
status: 200 OK
```

```
[{"person":{"id":77,"name":"Luis Thomas"},"workday":480,"sum_time_spent":3365,"workdays":7.01,"locked":false,"locked_days":"11111110000000000000000000000"},{"person":{"id":53,"name":"Frank Watson"},"workday":480,"sum_time_spent":10080,"workdays":21.0,"locked":true,"locked_days":"11111111111111111111111111111"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of timesheet settings.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of timesheets:

`person` `workday` `sum_time_spent` `workdays` `locked` `locked_days`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Sorting

A collection of timesheets is sorted **ascending** in the order they were generated.

## List incomplete timesheets

List all timesheets for an account which have not been completed for a specific week.

```
GET /timesheets/incomplete
```

The parameter `week_of` is required. This parameter is used to specify the week for which the timesheets are to be retrieved. A week can be selected by specifying any date of that week using the syntax `yyyy-mm-dd`. The parameter `organization_id` can be added to filter the results for a specific organization.

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X GET \
 "https://api.xurrent.com/v1/timesheets/incomplete?organization_id=44&week_of=2016-02-15"
```

### Response

```
status: 200 OK
```

```
[{"id":77,"name":"Luis Thomas","primary_email":"luis.thomas@widget.com","completeness":1,"remaining_time":673},{"id":54,"name":"Grace Weller","primary_email":"grace.weller.com","completeness":0,"remaining_time":2400},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of timesheet settings.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of timesheets:

`id` `name` `primary_email` `completeness` `remaining_time`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

## Get a single timesheet

Retrieve someone’s timesheet for a specific month.

```
GET /timesheets
```

The parameter `person_id` is required to ensure that the timesheet of a specific person is retrieved. In addition, the parameter `month_of` is required. This parameter is used to specify the month for which the person’s timesheet is to be retrieved. A month can be selected by specifying any date of that month using the syntax `yyyy-mm-dd`.

A person can have multiple timesheets for one month when the person switched to a different organization during the month. By specifying both the `person_id` and the `organization_id` it is possible to retrieve only the person’s timesheet that belongs to the specified organization.

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X GET \
 "https://api.xurrent.com/v1/timesheets?organization_id=44&person_id=77&month_of=2016-02-15"
```

### Response

```
status: 200 OK
```

```
{"person":{"id":77,"name":"Luis Thomas"},"workday":480,"sum_time_spent":3365,"workdays":7.01,"locked":false,"locked_days":"11111110000000000000000000000"}
```

The response contains [these fields](index.html#fields).

## Get day totals

Retrieve the total time that a person has spent on a specific day, or on each day of a specific week or month.

```
GET /timesheets/day_totals
```

The parameter `person_id` is required to ensure that the timesheet of a specific person is retrieved. In addition, the parameter `date`, `week_of` or `month_of` is required. One of these parameters is used to specify the date or dates for which the person’s total time spent is to be retrieved. A date can be specified using the syntax `yyyy-mm-dd`. A week or month can be selected by specifying any date of that week or month using the syntax `yyyy-mm-dd`.

Examples:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X GET \
 "https://api.xurrent.com/v1/timesheets/day_totals?person_id=77&date=2016-02-15"
```

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X GET \
 "https://api.xurrent.com/v1/timesheets/day_totals?person_id=77&week_of=2016-02-15"
```

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X GET \
 "https://api.xurrent.com/v1/timesheets/day_totals?person_id=77&month_of=2016-02-15"
```

When a person switched to a different organization on a specific date, then this person may have registered time entries on that date for different organizations. By specifying both the `person_id` and the `organization_id` it is possible to retrieve only the time that the person spent working for a specific organization.

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X GET \
 "https://api.xurrent.com/v1/timesheets/day_totals?organization_id=44&person_id=77&week_of=2016-02-15"
```

```
status: 200 OK
```

```
{"2016-02-15":"480","2016-02-16":"25","...":"..."}
```

## Lock dates

Lock a specific day, or lock each day of a specific week or month, for an organization or person.

```
POST /timesheets/lock
```

The parameter `organization_id` or `person_id` is required to ensure that the date or dates are locked only for the people of a specific organization or for a specific person. In addition, the parameter `date`, `week_of` or `month_of` is required. One of these parameters is used to specify the date or dates that need to be locked. A date can be specified using the syntax `yyyy-mm-dd`. A week or month can be selected by specifying any date of that week or month using the syntax `yyyy-mm-dd`.

Examples:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X POST \
 "https://api.xurrent.com/v1/timesheets/lock?person_id=77&date=2016-02-15"
```

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X POST \
 "https://api.xurrent.com/v1/timesheets/lock?person_id=77&week_of=2016-02-15"
```

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X POST \
 "https://api.xurrent.com/v1/timesheets/lock?person_id=77&month_of=2016-02-15"
```

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X POST \
 "https://api.xurrent.com/v1/timesheets/lock?organization_id=44&month_of=2016-02-15"
```

When a person switched to a different organization on a specific date, then it may be necessary to lock only the date(s) for one of the organizations that this person worked of. By specifying both the `person_id` and the `organization_id` it is possible to lock someone’s date(s) for a specific organization only.

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X POST \
 "https://api.xurrent.com/v1/timesheets/lock?organization_id=44&person_id=77&date=2016-02-15"
```

### Response

```
status: 204 No Content
```

## Unlock dates

Unlock a specific day, or unlock each day of a specific week or month, for an organization or person.

```
DELETE /timesheets/lock
```

The parameter `organization_id` or `person_id` is required to ensure that the date or dates are unlocked only for the people of a specific organization or for a specific person. In addition, the parameter `date`, `week_of` or `month_of` is required. One of these parameters is used to specify the date or dates that need to be unlocked. A date can be specified using the syntax `yyyy-mm-dd`. A week or month can be selected by specifying any date of that week or month using the syntax `yyyy-mm-dd`.

Examples:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X DELETE \
 "https://api.xurrent.com/v1/timesheets/lock?person_id=77&date=2016-02-15"
```

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X DELETE \
 "https://api.xurrent.com/v1/timesheets/lock?person_id=77&week_of=2016-02-15"
```

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X DELETE \
 "https://api.xurrent.com/v1/timesheets/lock?person_id=77&month_of=2016-02-15"
```

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X DELETE \
 "https://api.xurrent.com/v1/timesheets/lock?organization_id=44&month_of=2016-02-15"
```

When a person switched to a different organization on a specific date, then it may be necessary to unlock only the date(s) for one of the organizations that this person worked of. By specifying both the `person_id` and the `organization_id` it is possible to unlock someone’s date(s) for a specific organization only.

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X DELETE \
 "https://api.xurrent.com/v1/timesheets/lock?organization_id=44&person_id=77&date=2016-02-15"
```

### Response

```
status: 204 No Content
```

## Fields

completeness
: *Readonly* **[integer](../general/data_types.html)** — The Completeness field is set to `false` or `0` when the `sum_time_spent` of the timesheet is zero. It is set to `true` or `1` when some (but not all). This field is available only when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the person for whom the timesheet was generated. This field is available only when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

locked
: *Readonly* **[boolean](../general/data_types.html)** — The Locked field is set to `true` when all days of the selected month are locked for the selected person. It is set to `false` when there are still one or more unlocked days. This field is not available when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

locked\_days
: *Readonly* **[string](../general/data_types.html)** — The Locked field contains a string of booleans. The number of booleans is equal to the numbers of days in the selected month. A boolean is set to `0` when the corresponding date is unlocked; it is set to `1` when the corresponding date is locked. For example, when the value is `11111110000000000000000000000`, then the first 7 days of the month (February 2016) are locked, the rest are unlocked. This field is not available when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

name
: *Readonly* **[string](../general/data_types.html) (max 128)** — The Name of the person for whom the timesheet was generated. This field is available only when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

person
: *Readonly* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The person for whom the timesheet was generated. This field is not available when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

primary\_email
: *Readonly* **[string](../general/data_types.html) (max 128)** — The Primary email address of the person for whom the timesheet was generated. This field is available only when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

remaining\_time
: *Readonly* **[integer](../general/data_types.html)** — The difference between the number of minutes of a workweek (as specified in the timesheet settings of the organization), minus the total number of minutes of time spent that is specified in the person’s time entries for the selected week. This field is available only when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

sum\_time\_spent
: *Readonly* **[integer](../general/data_types.html)** — The total number of minutes of time spent that is specified in the person’s time entries for the selected month. This field is not available when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

workday
: *Readonly* **[integer](../general/data_types.html)** — The number of minutes of a workday as specified in the timesheet settings of the organization. This field is not available when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).

workdays
: *Readonly* **[decimal](../general/data_types.html)** — The total number of minutes of time spent that is specified in the person’s time entries for the selected month, divided by the number of minutes of a workday as specified in the timesheet settings of the organization. This field is not available when retrieving [incomplete timesheets](index.html#list-incomplete-timesheets).
