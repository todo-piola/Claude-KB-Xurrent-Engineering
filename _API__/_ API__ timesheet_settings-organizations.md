# Timesheet Settings - Organizations API

## List all organizations of a timesheet settings

List all [organizations](../../organizations.html) of a timesheet settings with a specific ID.

```
GET /timesheet_settings/:id/organizations
```

### Response

```
status: 200 OK
```

```
[{"id":44,"sourceID":null,"name":"Widget Data Center, External IT","parent":{"id":6,"name":"Widget Data Center"},"manager":{"id":6,"name":"Howard Tanner"},"created_at":"2016-03-22T21:02:50-05:00","updated_at":"2016-03-25T16:54:52-05:00"},{"id":50,"sourceID":null,"name":"Widget North America, Finance","parent":{"id":51,"name":"Widget North America, Inc."},"manager":{"id":120,"name":"Carolyn Goldrat"},"created_at":"2016-03-22T21:02:50-05:00","updated_at":"2016-03-22T21:03:36-05:00"},"..."]
```

The response contains [these fields](../../organizations.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/timesheet_settings/:id/organizations/disabled`: List all disabled organizations of a timesheet settings with a specific ID
- `/timesheet_settings/:id/organizations/enabled`: List all enabled organizations of a timesheet settings with a specific ID

## Add an organization to a timesheet settings

Add a link between a timesheet settings with a specific ID and an organization with a specific ID.

```
POST /timesheet_settings/:id/organizations/:organization_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove an organization from a timesheet settings

Remove the link between a timesheet settings with a specific ID and an organization with a specific ID.

```
DELETE /timesheet_settings/:id/organizations/:organization_id
```

### Response

```
status: 204 No Content
```

## Remove all organizations from a timesheet settings

Remove all links between a timesheet settings with a specific ID and its organizations.

```
DELETE /timesheet_settings/:id/organizations
```

### Response

```
status: 204 No Content
```
