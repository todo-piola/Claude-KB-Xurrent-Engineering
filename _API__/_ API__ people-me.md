# Me API

The services under the `/me` endpoint show items for the currently authenticated person.

## Me

List all details of the authenticated person.

```
GET /me
```

### Response

```
status: 200 OK
```

```
{"picture_uri":"https://itrp-demo.s3.amazonaws.com/defaults/avatars/people/large/5-430134.png","source":null,"information":"Experience & Interests:\n* PRINCE II/PMP\n* ISO 20000-1, ISO 20000-2 (ITIL)\n* ISO 17799","sourceID":null,"id":5,"created_at":"2016-02-17T09:17:51-06:00","disabled":false,"time_zone":"Central Time (US & Canada)","locale":"en-GB","primary_email":"howard.tanner@widget.com","manager":null,"job_title":"IT Manager (also Change Controller and Operations Manager)","supportID":"430134","name":"Howard Tanner","location":"Room 202, Desk 01","cost_per_hour":"100.0","updated_at":"2016-02-23T04:12:18-06:00","time_format_24h":false,"site":{"id":13,"name":"Widget Data Center"},"organization":{"id":30,"name":"Widget Data Center, External IT"},"contacts":[{"id":330,"telephone":"+1 (713) 987 2951","label":"work"},{"id":328,"telephone":"+1 (713) 441 8299","label":"mobile"},{"id":329,"telephone":"+1 (713) 987 2911","label":"fax"}],"account":{"name":"Widget Data Center","id":"wdc"},"addresses":[]}
```

## My Inbox

List all items of the authenticated person that are in his/her inbox.

```
GET /me/my_inbox
```

### Response

```
status: 200 OK
```

```
[{"task":{"for":{"organization":{"id":30,"name":"Widget Data Center, External IT"},"requester":{"id":68,"name":"Carla Cluster"}},"subject":"Inform service owner of implemented emergency change","team":{"id":11,"name":"Operations"},"next_target_at":"2016-02-23T12:00:44-06:00","new_assignment":true,"id":21413,"member":{"id":5,"name":"Howard Tanner"},"status":"assigned","impact":"none"}},{"request":{"for":{"organization":{"id":30,"name":"Widget Data Center, External IT"},"requester":{"id":72,"name":"Barney Turban"}},"subject":"Laptop CMP00035 will not boot any more","team":{"id":11,"name":"Operations"},"next_target_at":"best_effort","new_assignment":false,"id":70468,"member":{"id":5,"name":"Howard Tanner"},"status":"accepted","impact":"medium"}},"..."]
```

### Sorting

By default a collection of inbox items is sorted **descending** by `next_target_id`.

## My Team’s Inbox

List all items of the authenticated person that are in his/her team’s inbox.

```
GET /me/my_teams_inbox
```

### Response

```
status: 200 OK
```

```
[{"task":{"for":{"organization":{"id":30,"name":"Widget Data Center, External IT"},"requester":{"id":68,"name":"Carla Cluster"}},"subject":"Inform service owner of implemented emergency change","team":{"id":11,"name":"Operations"},"next_target_at":"2016-02-23T12:00:44-06:00","new_assignment":true,"id":21413,"member":{"id":5,"name":"Howard Tanner"},"status":"assigned","impact":"none"}},{"request":{"for":{"organization":{"id":30,"name":"Widget Data Center, External IT"},"requester":{"id":72,"name":"Barney Turban"}},"status":"in_progress","team":{"name":"Operations","id":11},"new_assignment":false,"subject":"Add monitoring job for IIS service on CMP00045","id":70416,"next_target_at":"best_effort","impact":null,"member":{"name":"Ellen Brown","id":47}}},"..."]
```

### Sorting

By default a collection of inbox items is sorted **descending** by `next_target_id`.

## Requests Requested By or For Me

List all Requests that were requested by or for the authenticated person.

```
GET /me/requested_by_or_for_me
```

### Response

```
status: 200 OK
```

```
[{"id":70417,"subject":"Remove monitoring jobs from CMP00041","created_at":"2016-02-15T13:14:00-06:00","status":"assigned","completed_at":null,"...":"..."},"...",{"id":70388,"subject":"No network on iPhone at Widget Data Center","created_at":"2016-02-10T10:29:00-06:00","status":"completed","completed_at":"2016-02-10T12:58:00-06:00","...":"..."},"..."]
```

### Sorting

By default this list is sorted by showing the open requests first **descending** by `id`, then showing the completed requests **descending** by `completed_at`.
