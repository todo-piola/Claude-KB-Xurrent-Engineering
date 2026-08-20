# People - Skill Pools API

## List all skill pools of a person

List all [skill pools](../../skill_pools/index.html) of a person with a specific ID.

```
GET /people/:id/skill_pools
```

### Response

```
status: 200 OK
```

```
[{"name":"Chief Financial Controllers","created_at":"2016-03-14T03:10:36-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:36-06:00","id":7,"disabled":false},{"name":"Expense Reporting SMEs","created_at":"2016-03-14T03:10:36-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:36-06:00","id":8,"disabled":false},"..."]
```

The response contains [these fields](../../skill_pools/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/people/:id/skill_pools/disabled`: List all disabled skill pools of a person with a specific ID
- `/people/:id/skill_pools/enabled`: List all enabled skill pools of a person with a specific ID

## Add a skill pool to a person

Add a link between a person with a specific ID and a skill pool with a specific ID.

```
POST /people/:id/skill_pools/:skill_pool_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a skill pool from a person

Remove the link between a person with a specific ID and a skill pool with a specific ID.

```
DELETE /people/:id/skill_pools/:skill_pool_id
```

### Response

```
status: 204 No Content
```

## Remove all skill pools from a person

Remove all links between a person with a specific ID and its skill pools.

```
DELETE /people/:id/skill_pools
```

### Response

```
status: 204 No Content
```
