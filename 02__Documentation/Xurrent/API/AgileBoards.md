# Agile Boards API

- [List agile boards](index.html#list-agile-boards)
- [Get a single agile board](index.html#get-a-single-agile-board)
- [Create an agile board](index.html#create-an-agile-board)
- [Update an agile board](index.html#update-an-agile-board)
- [Fields](index.html#fields)

## List agile boards

List all agile boards for an account:

```
GET /agile_boards
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2021-03-11T06:25:54-06:00","id":2,"name":"Application Development","sourceID":null,"updated_at":"2021-03-11T06:25:54-06:00","...":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of agile boards.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/agile_boards/disabled`: List all disabled agile boards
- `/agile_boards/enabled`: List all enabled agile boards

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of agile boards:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `created_at` `updated_at` `disabled` `service_instance` `request_template`

### Sorting

By default a collection of agile boards is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at` `service_instance` `request_template`

## Get a single agile board

```
GET /agile_boards/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2021-03-11T06:25:54-06:00","id":2,"name":"Application Development","sourceID":null,"updated_at":"2021-03-11T06:25:54-06:00","...":"..."}
```

The response contains [these fields](index.html#fields).

## Create an agile board

```
POST /agile_boards
```

When creating a new agile board [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created agile board and is similar to the response in [Get a single agile board](index.html#get-a-single-agile-board).

## Update an agile board

```
PATCH /agile_boards/:id
```

When updating an agile board [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated agile board and is similar to the response in [Get a single agile board](index.html#get-a-single-agile-board).

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the agile board was created.

current\_sprint
: *Readonly* **[reference](../general/data_types.html#reference) to [Sprint](../sprints/index.html)** — The scrum sprint the agile board is currently linked to.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to enter a description of the agile board.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the agile board may no longer be related to other records.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the agile board.

manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field is used to select the manager or supervisor of the agile board. This person is able to maintain the information about the agile board.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the agile board.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the agile board. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the agile board. If the agile board has no updates it contains the `created_at` value.

request\_template
: *Optional* **[reference](../general/data_types.html#references) to [Request Template](../request_templates.html)** — The Request template field is used to select the [Request template](../request_templates.html) that must be used to generate a new request in a agile board.

service\_instance
: *Optional* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The Service instance field is used to select the [Service Instance](../service_instances/index.html) that should be used when creating requests in this agile board.
