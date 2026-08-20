# Risks - Organizations API

## List all organizations of a risk

List all [organizations](../../organizations.html) who are linked as an organization to a risk with a specific ID.

```
GET /risks/:id/organizations
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

- `/risks/:id/organizations/disabled`: List all disabled organizations of a risk with a specific ID
- `/risks/:id/organizations/enabled`: List all enabled organizations of a risk with a specific ID
- `/risks/:id/organizations/external`: List all external organizations of a risk with a specific ID
- `/risks/:id/organizations/internal`: List all internal organizations of a risk with a specific ID
- `/risks/:id/organizations/directory`: List all organizations of a risk with a specific ID registered in the directory account of the support domain account from which the data is requested
- `/risks/:id/organizations/support_domain`: List all organizations of a risk with a specific ID registered in the account from which the data is requested
- `/risks/:id/organizations/managed_by_me`: List all organizations of a risk with a specific ID which manager or substitute is the API user

## Add an organization to a risk

Add a link between a risk with a specific ID and an organization with a specific ID.

```
POST /risks/:id/organizations/:organization_id
```

### Response

```
status: 200 OK
```

```
{}
```

## Remove an organization from a risk

Remove the link between a risk with a specific ID and an organization with a specific ID.

```
DELETE /risks/:id/organizations/:organization_id
```

### Response

```
status: 204 No Content
```

## Remove all organizations from a risk

Remove all links between a risk with a specific ID and its organizations.

```
DELETE /risks/:id/organizations
```

### Response

```
status: 204 No Content
```
