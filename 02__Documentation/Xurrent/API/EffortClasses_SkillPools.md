# Effort Classes - Skill Pools API

## List all skill pools of an effort class

List all [skill pools](../../skill_pools/index.html) of an effort class with a specific ID.

```
GET /effort_classes/:id/skill_pools
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

- `/effort_classes/:id/skill_pools/disabled`: List all disabled skill pools of an effort class with a specific ID
- `/effort_classes/:id/skill_pools/enabled`: List all enabled skill pools of an effort class with a specific ID

## Add a skill pool to an effort class

Add a link between an effort class with a specific ID and a skill pool with a specific ID.

```
POST /effort_classes/:id/skill_pools/:skill_pool_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a skill pool from an effort class

Remove the link between an effort class with a specific ID and a skill pool with a specific ID.

```
DELETE /effort_classes/:id/skill_pools/:skill_pool_id
```

### Response

```
status: 204 No Content
```

## Remove all skill pools from an effort class

Remove all links between an effort class with a specific ID and its skill pools.

```
DELETE /effort_classes/:id/skill_pools
```

### Response

```
status: 204 No Content
```
