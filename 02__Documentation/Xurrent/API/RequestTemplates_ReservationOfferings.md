# Request Templates - Requests API

## List reservation offerings of a request template

List all [reservation offerings](../../reservation_offerings/index.html) of the request template with a specific ID.

```
GET /request_templates/:id/reservation_offerings
```

### Response

```
status: 200 OK
```

```
[{"id":7,"sourceID":null,"name":"4me training environment","created_at":"2020-07-09T20:34:33-05:00","updated_at":"2020-07-09T20:34:51-05:00","nodeID":"..."},{"id":24,"sourceID":null,"name":"Conference Rooms","created_at":"2020-07-10T20:24:05-05:00","updated_at":"2020-07-13T04:19:48-05:00","nodeID":"..."},{"id":25,"sourceID":null,"name":"Pool Car","created_at":"2020-07-11T17:38:13-05:00","updated_at":"2020-07-11T18:17:53-05:00","nodeID":"..."},"..."]
```

The response contains [these fields](../../reservation_offerings/index.html#collection-fields) by default.
