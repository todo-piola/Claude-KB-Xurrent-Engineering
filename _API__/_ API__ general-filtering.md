# Filtering

When requesting a collection of resources the resulting list can be reduced by passing one or more filter conditions:

```
$ curl https://api.xurrent.com/v1/requests?status=assigned\
 &next_target_at=>2011-10-01T00:00:00Z
```

Multiple conditions are joined using *AND*.

## Allowed filters

Not all fields can be filtered. The fields that support filtering are listed for each individual API.

If you need more extensive filtering capabilities, such as the capability to filter on custom fields,
please use the [Xurrent GraphQL API](https://developer.xurrent.com/graphql).

## Allowed operators

The following operators can be used in filter conditions:

equality
: Same as given value

 `?id=43523` or `?name=foo`

negation
: Different from given value

 `?status=!assigned` or `?team_id=!4`

empty
: Has no value (null)

 `?team_id=` or `?remarks=`

present
: Contains a value (not null)

 `?team_id=!` or `?remarks=!`

in
: Equal to one of the given values (*integers and enums only*)

 `?id=1,2,3,4` or `?ids=1,2,3,4` or `?status=assigned,accepted`

not in
: Not equal to one of the given values (*integers and enums only*)

 `?id=!1,2,3,4` or `?ids=!1,2,3,4` or `?status!=assigned,accepted`

less than
: Less than given value (*numeric and date/time types only*)

 `?created_at=<2016-01-15T23:00:00Z` or `?purchase_value=<90.00`

less than or equal to
: Less than or equal to given value (*numeric and date/time types only*)

 `?warranty_expiry_date=<=2016-01-15` or `?nr_of_licenses=<=30`

greater than
: Greater than given value (*numeric and date/time types only*)

 `?completed_at=>2016-01-15T23:00:00Z` or `?nr_of_processors=>2`

greater than or equal to
: Greater than or equal to given value (*numeric and date/time types only*)

 `?updated_at=>=2016-01-15T23:00:00Z` or `?salvage_value=>=100.00`

greater than and less than
: Greater than given value and less than the other given value (*numeric and date/time types only*)

 `?date=>2015-12-31<2016-02-01` or `?assignment_count=>3<10`

greater than or equal to and less than or equal to
: Greater than or equal to given value and less than or equal to the other given value (*numeric and date / time types only*)

 `?date=>=2016-01-01<=2016-01-31` or `?assignment_count=>=4<=9`

For date time target fields like response\_target\_at, resolution\_target\_at and next\_target\_at, the following special values are also accepted: `best_effort`, `clock_stopped`, `no_target`.

For string and text fields like `name` and `subject`, filtering is case sensitive, unless otherwise specified.

See the [Data Types](../data_types.html#input) section for more information on the formatting of input values.

## Filter Exceptions

Not all combinations of filters are allowed and not all operators can be used on all fields.
In case an invalid filter condition is applied a Bad Request response will be returned.

```
status: 400 Bad Request
content-type: application/json; charset=utf-8
```

```
{"message":"..."}
```

Some example messages are:

- “Field ‘disabled’ does not support the ‘=>’ operator”
- “Cannot apply the ‘=’ operator to a set of values for field ‘subject’”
- “Cannot filter on a set of values for field ‘disabled’”
- “Unknown fields: disabled, strange”
- “Filtering not allowed on fields: times\_applied”

## Predefined Filters

Most models have predefined filters, similar to the state buttons and views found in the Xurrent UI.
They can be applied by appending `/<predefined_filter>` to the URI path:

```
$ curl https://api.xurrent.com/v1/requests/open
```

Alternatively, the `?state=` parameter can be used to apply a predefined filter:

```
$ curl https://api.xurrent.com/v1/requests?state=open

$ curl https://api.xurrent.com/v1/requests/requested_by_or_for_me?state=open
```

It is possible to combine predefined filters and filter conditions.

It is also possible to use predefined filters to look up only certain relations of a specific record.
This make it possible to, for example, look up the open requests that are linked to a workflow, or the internal notes of a request.

```
$ curl https://api.xurrent.com/v1/workflows/:id/requests/open

$ curl https://api.xurrent.com/v1/requests/:id/notes/internal
```
