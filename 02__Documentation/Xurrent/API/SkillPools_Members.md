# Skill Pools - Members API

## List all members of a skill pool

List all [people](../../people.html) who are linked as a member to a skill pool with a specific ID.

```
GET /skill_pools/:id/members
```

### Response

```
status: 200 OK
```

```
[{"name":"Ashok Kumar","created_at":"2016-03-14T03:09:55-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:31-06:00","manager":{"name":"Howard Tanner","id":5},"id":30,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},{"name":"Barney Turban","created_at":"2016-03-14T03:09:57-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:32-06:00","manager":{"name":"Howard Tanner","id":5},"id":58,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},"..."]
```

The response contains [these fields](../../people.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/skill_pools/:id/members/disabled`: List all disabled members of a skill pool with a specific ID
- `/skill_pools/:id/members/enabled`: List all enabled members of a skill pool with a specific ID
- `/skill_pools/:id/members/internal`: List all internal members of a skill pool with a specific ID
- `/skill_pools/:id/members/directory`: List all members of a skill pool registered in the directory account of the support domain account from which the data is requested
- `/skill_pools/:id/members/support_domain`: List all members of a skill pool registered in the account from which the data is requested (and *not* the related directory account)

## Add a member to a skill pool

Add a link between a skill pool with a specific ID and a person with a specific ID to make this person a member of the skill pool.

```
POST /skill_pools/:id/members/:person_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove a member from a skill pool

Remove the membership link between a skill pool with a specific ID and a person with a specific ID.

```
DELETE /skill_pools/:id/members/:person_id
```

### Response

```
status: 204 No Content
```

## Remove all members from a skill pool

Remove all links between a skill pool with a specific ID and its members.

```
DELETE /skill_pools/:id/members
```

### Response

```
status: 204 No Content
```
