# Agile Boards - Columns API

- [List all columns of an agile board](../columns.html#list-all-columns-of-an-agile-board)
- [Get a single column of an agile board](../columns.html#list-all-columns-of-an-agile-board)
- [Add a column to an agile board](../columns.html#add-a-column-to-an-agile-board)
- [Update a column of an agile board](../columns.html#update-a-column-of-an-agile-board)
- [Remove a column from an agile board](../columns.html#remove-a-column-from-an-agile-board)
- [Fields](../columns.html#fields)

## List all columns of an agile board

List all columns of an agile board with a specific ID.

```
GET /agile_boards/:id/agile_board_columns
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2021-03-11T06:25:54-06:00","id":2,"name":"To Be Analyzed","updated_at":"2021-03-11T06:25:54-06:00","...":"..."},"..."]
```

The response contains [these fields](../columns.html#collection-fields) by default.

### Collection Fields

By default the following [fields](../columns.html#fields) will appear in collections of agile board columns:

`id` `name` `created_at` `updated_at`

Obtain a different set of [fields](../columns.html#fields) using the [?fields= parameter](../../general/field_selection/index.html#collection-of-resources).

## Get a single column of an agile board

```
GET /agile_boards/:id/agile_board_columns/:column_id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2021-03-11T06:25:54-06:00","id":2,"name":"To Be Analyzed","updated_at":"2021-03-11T06:25:54-06:00","...":"..."}
```

The response contains [these fields](../columns.html#fields).

## Add a column to an agile board

Add a column to an agile board with a specific ID.

```
POST /agile_boards/:id/agile_board_columns
```

When creating a new column for an agile board [these fields](../columns.html#fields) are available.

### Response

```
status: 201 Created
```

```
{}
```

## Update a column of an agile board

Update a column with a specific ID of an agile board with a specific ID.

```
PATCH /agile_boards/:id/agile_board_columns/:column_id
```

When updating an existing column of an agile board [these fields](../columns.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"In Progress","...":"..."}
```

## Remove a column from an agile board

Remove a column with a specific ID from an agile board with a specific ID.

```
DELETE /agile_boards/:id/agile_board_columns/:column_id
```

### Response

```
status: 204 No Content
```

## Fields

action\_type
: *Required* **[enum](../../general/data_types.html)**, default: `none` — The Action type field is used to specify
 what action is to be performed when an item is moved into the column. Valid values are:
: - `none`: None
 - `assign`: Set the status of the item to ‘Assigned’
 - `accept`: Set the status of the item to ‘Accepted’ and assign it to the current person
 - `start`: Set the status of the item to ‘In Progress’ and assign it to the current person
 - `complete`: Set the status of the item to ‘Completed’ and assign it to the current person

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the column was created.

clear\_member
: *Optional* **[boolean](../../general/data_types.html)** — The Clear member box is used to indicated that the member field should be cleared of items
 that are moved into the column. Only applicable when the `action_type` is equal to `assign`.

deleted
: *Readonly* **[boolean](../../general/data_types.html)** — The Deleted box is automatically checked after removing a column
 from a board. This happens only when the column has at any point in time contained 1 or more items.

dialog\_type
: *Required* **[enum](../../general/data_types.html)**, default: `none` — The Dialog type field is used to specify
 what kind of dialog is to be shown when an item is moved into the column. Valid values are:
: - `none`: None
 - `minimal`: Show a small dialog that contains a note field and, depending on the Action type of the column, a few other fields
 - `full`: Show a form with all the fields of the item

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the column.

member
: *Optional* **[reference](../../general/data_types.html#references) to [Person](../../people.html)** — The Member field is only applicable
 when the Team field of the column has a value, and indicates to which team member the item is to be assigned when it is moved into the column.

name
: *Required* **[string](../../general/data_types.html) (max 128)** — The Name field is used to enter the name of the column.

position
: *Optional* **[integer](../../general/data_types.html)** — The Position field is used to specify the position of the column,
 relative to the other columns of the agile board. The leftmost column has position 1.

remove\_after
: *Optional* **[integer](../../general/data_types.html)** — Items in this column that are not moved for the specified number of days are removed from the board.

team
: *Optional* **[reference](../../general/data_types.html#references) to [Team](../../teams.html)** — The Team field is only applicable
 when the Action type of the column is `assign`, and indicates to which team the item is to be assigned when it is moved into the column.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the column.
 If the column has no updates it contains the `created_at` value.

wip\_limit
: *Optional* **[integer](../../general/data_types.html)** — The Work In Progress (WIP) limit field is used to indicate
 the maximum number of items that are expected to be in the column at any point in time.
