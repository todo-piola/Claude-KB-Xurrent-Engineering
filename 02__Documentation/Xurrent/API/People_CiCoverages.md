# People - Configuration Item Coverages API

## List configuration item coverages of a person

List all [Configuration Items](../../configuration_items/index.html) that are related to a [Service Instance](../../service_instances/index.html) for which a person with a specific ID is covered by an [SLA](../../service_level_agreements.html). The result is limited to the CIs to which the person is linked as a user, plus the CIs that do not have any users linked to them.

```
GET /people/:id/ci_coverages
```

### Response

```
status: 200 OK
```

```
[{"name":"Adobe Reader 9.1.0","label":"Adobe Reader 9.1.0","created_at":"2016-03-14T03:11:22-06:00","sourceID":null,"updated_at":"2016-03-14T03:11:22-06:00","service":{"name":"Personal Computing","id":22,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"support_team":{"name":"End-User Support, Houston","id":9},"id":711,"product":{"name":"Adobe Reader","brand":"Adobe","category":"software/browser_viewer_application","id":33},"status":"in_production","software":true,"rule_set":"software"},"..."]
```

The response contains [these fields](../../configuration_items/index.html#collection-fields) by default.

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](../ci_coverages.html#/v1/configuration_items/#fields):

`status` `rule_set`
