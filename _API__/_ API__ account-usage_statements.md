# Account - Usage Statements API

- [List usage statements](index.html#list-usage-statements)
- [Get a usage statement](index.html#get-a-usage-statement)
- [Fields](index.html#fields)

Note: you must be account owner to access this API.

## List Usage Statements

List all usage statements:

```
GET /account/usage_statements
```

### Response

```
status: 200 OK
```

```
[{"id":1280,"plan":"premium_plus","year":2015,"month":10,"start_date":"2015-10-24","end_date":"2015-10-31","user_months":3},{"id":1432,"plan":"premium_plus","year":2015,"month":11,"start_date":"2015-11-01","end_date":"2015-11-30","user_months":12},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../../general/pagination.html) are available to reduce/limit the collection of usage statements.

### Collection Fields

By default the following [fields](index.html#fields) will appear collections of usage statements:

`end_date` `id` `month` `plan` `start_date` `user_months` `year`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `year` `month`

### Sorting

By default a collection of usage statements is sorted **descending** by `id`.

## Get a Usage Statement

```
GET /account/usage_statements/:id
```

The following can be used to get the usage statement for October 2015:

```
GET /account/usage_statements?year=2015&month=10
```

### Response

```
status: 200 OK
```

```
{"billable_user_ids":[1205,1206,1207,1208,1209,1210,1211,1212,1275,1267,1271,1264],"end_date":"2015-11-30","id":1432,"month":11,"plan":"premium_plus","start_date":"2015-11-01","user_months":12,"year":2015}
```

The response contains [these fields](index.html#fields).

## Fields

billable\_user\_ids
: *Readonly* **array of [references](../../general/data_types.html#references) to [Person](../../people.html)** — The IDs of the Person records that are registered in the account and which were enabled and had a role (other than End User or Key Contact) at any time between the start date and the end date.

end\_date
: *Readonly* **[date](../../general/data_types.html)** — The date on which the billing period ended.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the usage statement.

month
: *Readonly* **[integer](../../general/data_types.html)** — The month for which the usage statement was generated.

plan
: *Readonly* **[enum](../../general/enumerations/index.html)** — The Plan field is used to select the Plan for the account. Valid values are:
: - `basic`
 - `premium`
 - `premium_plus`

start\_date
: *Readonly* **[date](../../general/data_types.html)** — The date on which the billing period started.

user\_months
: *Readonly* **[integer](../../general/data_types.html)** — The number of Person records that are registered in the account and which were enabled and had a role (other than End User or Key Contact) at any time between the start date and the end date.

year
: *Readonly* **[integer](../../general/data_types.html)** — The year for which the usage statement was generated.
