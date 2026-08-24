# Teams API

- [List teams](../teams.html#list-teams)
- [Get a single team](../teams.html#get-a-single-team)
- [Create a team](../teams.html#create-a-team)
- [Update a team](../teams.html#update-a-team)
- [Fields](../teams.html#fields)

## List teams

List all teams for an account:

```
GET /teams
```

### Response

```
status: 200 OK
```

```
[{"name":"Application Development","created_at":"2016-03-14T03:10:36-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:36-06:00","id":7,"disabled":false},{"name":"Database Administration","created_at":"2016-03-14T03:10:36-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:36-06:00","id":8,"disabled":false},"..."]
```

The response contains [these fields](../teams.html#collection-fields) by default. [Filtering](../teams.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of teams.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/teams/disabled`: List all disabled teams
- `/teams/enabled`: List all enabled teams

### Collection Fields

By default the following [fields](../teams.html#fields) will appear in collections of teams:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](../teams.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../teams.html#fields):

`id` `source` `sourceID` `name` `created_at` `updated_at` `disabled`

### Sorting

By default a collection of teams is sorted **ascending** by `name`.

The following [fields](../teams.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single team

```
GET /teams/:id
```

### Response

```
status: 200 OK
```

```
{"picture_uri":null,"name":"Application Development","coordinator":{"name":"Frank Watson","id":32},"remarks":"Responsible for all non-SAP server-based applications of the Widget Data Center organization.","created_at":"2016-03-14T03:10:36-06:00","sourceID":null,"work_hours":{"name":"Monday through Friday, 8:00am until 5:00pm","id":38},"updated_at":"2016-03-14T03:10:36-06:00","manager":{"name":"Rodney Wilson","id":34},"configuration_manager":{"name":"Frank Watson","id":32},"id":7,"time_zone":"Central Time (US & Canada)","disabled":false,"source":null,"inbound_email_local_part":"application-development"}
```

The response contains [these fields](../teams.html#fields).

## Create a team

```
POST /teams
```

When creating a new team [these fields](../teams.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"configuration_manager":"...","...":"..."}
```

The response contains [all fields](../teams.html#fields) of the created team and is similar to the response in [Get a single team](../teams.html#get-a-single-team)

## Update a team

```
PATCH /teams/:id
```

When updating a team [these fields](../teams.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"configuration_manager":"...","...":"..."}
```

The response contains [all fields](../teams.html#fields) of the updated team and is similar to the response in [Get a single team](../teams.html#get-a-single-team)

## Fields

agile\_board
: *Optional* **[reference](../general/data_types.html#references) to [Agile Board](../agile_boards/index.html)** — The Agile Board field is used to automatically link records to the agile board when they are assigned to the team.

auto\_assign
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Auto assign field is used to indicate whether requests are auto-assigned to a team member.

attachments
: *Readonly* **aggregated Attachments**

configuration\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Configuration manager field is used to select the person who maintains the information about the [Configuration Items](../configuration_items/index.html) that the team supports.

coordinator
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Coordinator field is used to select the current team coordinator for the team. Only members of the team can be selected in this field.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the team was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the team.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the team may no longer be related to other records.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the team.

inbound\_email\_local\_part
: *Optional* **[string](../general/data_types.html) (max 64)** - The Inbound email address field is used to specify an email address for the team. When an email is sent to this email address, a new request gets generated and assigned to the team. Visit [Xurrent Mail API](../requests/mail.html) for more information about inbound email.

manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field is used to select the manager or supervisor of the team. This person is able to maintain the information about the team. The manager of a team does not need to be a member of the team.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the team.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the team. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the team that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Remarks field.

scrum\_workspace
: *Readonly* **[reference](../general/data_types.html#references) to [Scrum Workspace](https://developer.xurrent.com/v1/teams/v1/scrum_workspaces/)** — The Scrum Workspace used by this team to plan their work.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

time\_zone
: *Optional* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the selected work hours.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the team. If the team has no updates it contains the `created_at` value.

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the team.

work\_hours
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Work hours field is used to select a [Calendar](../calendars/index.html) that defines the work hours during which the team is available for work on all types of assignments.
