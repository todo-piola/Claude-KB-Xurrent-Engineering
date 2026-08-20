# Calendars API

- [List calendars](index.html#list-calendars)
- [Get a single calendar](index.html#get-a-single-calendar)
- [Get a duration](index.html#get-a-duration)
- [Create a calendar](index.html#create-a-calendar)
- [Update a calendar](index.html#update-a-calendar)
- [Fields](index.html#fields)

## List calendars

List all calendars for an account:

```
GET /calendars
```

### Response

```
status: 200 OK
```

```
[{"name":"24x5 (Monday through Friday)","created_at":"2016-03-14T03:09:47-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:47-06:00","id":32,"calendar_hours":[{"time_until":"00:00","time_from":"00:00","weekday":"mon"},{"time_until":"00:00","time_from":"00:00","weekday":"tue"},{"time_until":"00:00","time_from":"00:00","weekday":"wed"},{"time_until":"00:00","time_from":"00:00","weekday":"thu"},{"time_until":"00:00","time_from":"00:00","weekday":"fri"}],"source":null,"disabled":true},{"name":"24x6 (Monday through Saturday)","created_at":"2016-03-14T03:09:47-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:47-06:00","id":33,"calendar_hours":[{"time_until":"00:00","time_from":"00:00","weekday":"mon"},{"time_until":"00:00","time_from":"00:00","weekday":"tue"},{"time_until":"00:00","time_from":"00:00","weekday":"wed"},{"time_until":"00:00","time_from":"00:00","weekday":"thu"},{"time_until":"00:00","time_from":"00:00","weekday":"fri"},{"time_until":"00:00","time_from":"00:00","weekday":"sat"}],"source":null},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of calendars.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/calendars/disabled`: List all disabled calendars
- `/calendars/enabled`: List all enabled calendars

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of calendars:

`id` `source` `sourceID` `name` `calendar_hours` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `sourceID` `name` `disabled` `created_at` `updated_at`

The filters on `sourceID` and `name` are not case sensitive.

### Sorting

By default a collection of calendars is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single calendar

```
GET /calendars/:id
```

### Response

```
status: 200 OK
```

```
{"name":"24x5 (Monday through Friday)","created_at":"2016-03-14T03:09:47-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:47-06:00","disabled":false,"id":32,"calendar_hours":[{"time_until":"00:00","time_from":"00:00","weekday":"mon"},{"time_until":"00:00","time_from":"00:00","weekday":"tue"},{"time_until":"00:00","time_from":"00:00","weekday":"wed"},{"time_until":"00:00","time_from":"00:00","weekday":"thu"},{"time_until":"00:00","time_from":"00:00","weekday":"fri"}],"source":null}
```

The response contains [these fields](index.html#fields).

## Get a duration

Calculate the duration between a start and end time for a specific calendar:

```
GET /calendars/:id/duration/?start=:time&end=:time&time_zone=:timezone"
```

The API returns the number of minutes between the start and end, including only the time during which the calendar is active and excluding any [holidays](../holidays.html) that are linked to the calendar.

The time zone that is to be applied to the calendar is optional. If a time zone is not specified, the default UTC time zone is applied.

### Examples

The total number of calendar minutes for the month of January 2020:

```
 $ curl -u "api-token:x" -X GET -H "X-Xurrent-Account: wdc" https://api.xurrent.com/v1/calendars/42/duration?start=2020-01-01T00:00:00Z&end=2020-02-01T00:00:00Z
```

The number of calendar minutes between 9am and 5pm Eastern Time (which is GMT-05:00) on January 20, 2020 where the time zone for the calendar is Central Time (which is GMT-06:00):

```
 $ curl -u "api-token:x" -X GET -H "X-Xurrent-Account: wdc" -d '{"start":"2020-01-20T09:00:00-05:00", "end":"2020-01-20T17:00:00-05:00", "time_zone":"Central Time (US & Canada)"}' "https://api.xurrent.com/v1/calendars/42/duration"
```

## Create a calendar

```
POST /calendars
```

When creating a new calendar [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"calendar_hours":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created calendar and is similar to the response in [Get a single calendar](index.html#get-a-single-calendar)

## Update a calendar

```
PATCH /calendars/:id
```

When updating a calendar [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"calendar_hours":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated calendar and is similar to the response in [Get a single calendar](index.html#get-a-single-calendar)

## Fields

calendar\_hours
: *Readonly* **aggregated calendar hours**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the calendar was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the calendar may no longer be related to other records.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the calendar.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the calendar.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the calendar. If the calendar has no updates it contains the `created_at` value.
