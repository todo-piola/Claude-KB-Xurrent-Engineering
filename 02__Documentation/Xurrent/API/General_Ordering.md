# Ordering

Collections of resources are always ordered. Therefore each model defines a *default sort order*.
Usually this is ascending by `name` (e.g. for Services) or descending by `id` (e.g. for Requests).

To change the ordering provide the `?sort=` parameter. Multiple fields must be separated with a comma.
Fields are sorted in ascending order, unless they are prepended with a minus sign.

```
$ curl https://api.xurrent.com/v1/requests?sort=-status,impact,-id
```

Only a subset of the available fields may be used. If a different field is provided a Bad Request response will be returned.
The documentation on that specific resource defines the *sortable fields*.

```
$ curl https://api.xurrent.com/v1/requests?sort=problem
```

```
status: 400 Bad Request
content-type: application/json; charset=utf-8
```

```
{"message":"Sorting not allowed on fields: problem"}
```
