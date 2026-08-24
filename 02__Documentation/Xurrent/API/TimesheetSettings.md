# Timesheet Settings API

- [List timesheet settings](index.html#list-timesheet-settings)
- [Get a single timesheet settings](index.html#get-a-single-timesheet-settings)
- [Create a timesheet settings](index.html#create-a-timesheet-settings)
- [Update a timesheet settings](index.html#update-a-timesheet-settings)
- [Fields](index.html#fields)

## List timesheet settings

List all timesheet settings for an account:

```
GET /timesheet_settings
```

### Response

```
status: 200 OK
```

```
[{"id":321,"sourceID":null,"name":"8hr workday, 40hr workweek, hours&minutes, 1hr incr.","created_at":"2016-03-22T21:03:35-05:00","updated_at":"2016-03-22T21:03:35-05:00"},{"id":485,"sourceID":null,"name":"7:30 workday, 36hr workweek, hours&minutes, 0:30 incr.","created_at":"2016-03-27T18:53:12-05:00","updated_at":"2016-03-28T22:56:03-05:00"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of timesheet settings.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/timesheet_settings/enabled`: List all enabled timesheet settings
- `/timesheet_settings/disabled`: List all disabled timesheet settings

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of timesheet settings:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `created_at` `updated_at` `disabled`

The filters on `source`, `sourceID` and `name` are not case sensitive.

### Sorting

By default a collection of timesheet settings is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single timesheet settings

```
GET /timesheet_settings/:id
```

### Response

```
status: 200 OK
```

```
{"disabled":false,"allocation_time_tracking":true,"allow_workday_overtime":false,"allow_workweek_overtime":false,"assignment_time_tracking":true,"id":485,"name":"7:30 workday, 36hr workweek, hours&minutes, 0:30 incr.","percentage_increment":null,"source":null,"sourceID":null,"time_increment":30,"unit":"hours_and_minutes","workday":450,"workweek":2160,"created_at":"2016-03-27T18:53:12-05:00","updated_at":"2016-03-28T22:56:03-05:00"}
```

The response contains [these fields](index.html#fields).

## Create a timesheet settings

```
POST /timesheet_settings
```

When creating a new timesheet settings [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"coverage":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created timesheet settings and is similar to the response in [Get a single timesheet settings](index.html#get-a-single-timesheet-settings)

## Update a timesheet settings

```
PATCH /timesheet_settings/:id
```

When updating a timesheet settings [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated timesheet settings and is similar to the response in [Get a single timesheet settings](index.html#get-a-single-timesheet-settings)

## Fields

allocation\_time\_tracking
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Allocation time tracking box is checked when people of the related organizations need to be able to register time entries for the time allocations that are linked to their organizations.

allow\_workday\_overtime
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Allow workday overtime box is checked when the people of the organizations to which the timesheet settings are linked are allowed to register more time for a single day than the amount of time specified in the Workday field.

allow\_workweek\_overtime
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Allow workweek overtime box is checked when the people of the organizations to which the timesheet settings are linked are allowed to register more time for a single week than the amount of time specified in the Workweek field.

assignment\_time\_tracking
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Assignment time tracking box is checked when the Time spent field needs to be available in requests, problems and tasks for specialists of the related organizations to specify how long they have worked on their assignments.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the timesheet settings was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the timesheet settings may no longer be related to any more organizations.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the timesheet settings.

name
: *Required* **[string](../general/data_types.html) (max 160)** — The Name field is used to enter the name of the timesheet settings.

notify\_on\_incomplete
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The ‘Notify people when their timesheet is incomplete’ checkbox prevents Xurrent from sending notifications to people whose timesheet is incomplete.

percentage\_increment
: *Optional* **[enum](../general/data_types.html)**, default: `12.5` — The Percentage Increment field is used to select the minimum amount percentage of a workday that the people of the organizations to which the timesheet settings are linked can select when they register a time entry. This percentage of a workday is also the increment by which they can increase this minimum percentage of a workday. Valid values are:
: - `12.5`: 12.5%
 - `25`: 25%
 - `50`: 50%
 - `100`: 100%

problem\_effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The effort class that is selected by default, when someone in an organization linked to the timesheet settings registers time on a problem.

project\_task\_effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The effort class that is selected by default, when someone in an organization linked to the timesheet settings registers time on a project task.

request\_effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The effort class that is selected by default, when someone in an organization linked to the timesheet settings registers time on a request.

require\_note
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Require note box is checked when the Note field needs to become required, when someone in an organization linked to the timesheet settings registers time on a request, problem or task.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

task\_effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The effort class that is selected by default, when someone in an organization linked to the timesheet settings registers time on a workflow task.

time\_allocation\_effort\_class
: *Optional* **[reference](../general/data_types.html#references) to [Effort Class](../effort_classes.html)** — The effort class that is selected by default, when someone in an organization linked to the timesheet settings registers time on a time allocation.

time\_increment
: *Optional* **[integer](../general/data_types.html)**, default: `60` — The Time Increment field is used to select the minimum amount of time that the people of the organizations to which the timesheet settings are linked can select when they register a time entry. This amount of time is also the increment by which they can increase this minimum amount of time. Allowed values are: `5`, `10`, `15`, `30`, `60`, `120`, `240`.

unit
: *Required* **[enum](../general/data_types.html)**, default: `hours_and_minutes` — The Unit field is used to specify whether the people of the organizations to which the timesheet settings are linked need to register their time in hours and minutes, or as a percentage of a workday. Valid values are:
: - `hours_and_minutes`: Hours & Minutes
 - `percentage_of_workday`: Percentage of Workday

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the timesheet settings. If the timesheet settings has no updates it contains the `created_at` value.

workday
: *Optional* **[integer](../general/data_types.html)**, default: `480` — The Workday field is used to specify the duration of a workday in minutes.

workweek
: *Optional* **[integer](../general/data_types.html)**, default: `2400` — The Workweek field is used to specify the duration of a workweek in minutes.
