# Requests - Affected SLAs API

## List affected SLAs of a request

List all [affected SLAs](../../affected_slas/index.html) of the request with a specific ID.

```
GET /requests/:id/affected_slas
```

### Response

```
status: 200 OK
```

```
[{"stopped_clock_at":null,"service_instance":{"name":"New York Network","id":73},"created_at":"2016-03-14T03:00:11-06:00","started_at":"2016-03-14T03:00:11-06:00","support_hours":{"name":"24x7 (Monday through Sunday)","id":29},"downtime_start_at":null,"actual_response_at":"2016-03-14T03:00:11-06:00","actual_resolution_duration":0,"updated_at":"2016-03-14T03:14:11-06:00","supplier":null,"stopped_clock_duration":0,"resolution_target_at":"2016-03-14T13:00:11-06:00","actual_response_duration":0,"support_team":{"name":"Operations","id":11},"response_target_at":"2016-03-14T04:00:11-06:00","id":214,"request":{"account":{"name":"Widget North America","id":"wna"},"id":70473,"subject":"Windows password reset required"},"downtime_duration":null,"downtime_end_at":null,"accountability":"supplier","time_zone":"Central Time (US & Canada)","sla":{"name":"End-User Network Connectivity for Widget North America, HQ (New York)","id":34},"impact":"medium","service_hours":null,"maximum_response_duration":60,"maximum_resolution_duration":600,"actual_resolution_at":"2016-03-14T03:00:11-06:00","first_line_team":null,"standard_service_request":null},"..."]
```

The response contains [these fields](../../affected_slas/index.html#collection-fields) by default.
