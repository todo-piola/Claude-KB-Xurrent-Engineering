# Field Selection

## Single Resource

The JSON result for a single resource will always contain all fields. These fields are composed of:

1. simple properties, like `id`, `name` and `location`
2. single [references](../data_types.html#references), like `site` and `organization`
3. collections of [references](../data_types.html#references), like `addresses` and `contacts`

Note that the properties and single references may be `null` and that collections of references may be empty.

```
 $ curl https://api.xurrent.com/v1/people/15
```

```
status: 200 OK
```

```
{"picture_uri":"https://itrp-demo.s3.amazonaws.com/defaults/avatars/people/large/2-56089.png","name":"Susan Spoc","location":"Cubicle P2-314","created_at":"2016-03-30T11:26:45Z","sourceID":null,"primary_email":"susan.spoc@virtualsupport.com","job_title":"Service Desk Analyst","addresses":[],"updated_at":"2016-03-30T11:27:21Z","account":{"name":"VirtualSupport","id":"virtualsupport"},"manager":{"name":"Khunal Shrestra","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":2},"information":"Susan can act as a service desk analyst for Widget North America and Widget Data Center.","id":15,"site":{"name":"VirtualSupport Global Support Center","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":4},"organization":{"name":"VirtualSupport, Ltd.","account":{"name":"VirtualSupport","id":"virtualsupport"},"id":2},"disabled":false,"contacts":[{"label":"work","id":301,"telephone":"+91 (80) 2547 7154"},{"label":"fax","id":300,"telephone":"+91 (80) 2547 7101"}],"source":null}
```

### Account

When the account of the resource is different from the account of the authenticated user,
the `account` [reference](../data_types.html#references) will be provided.

## Collection of Resources

When requesting a collection of resources only the default fields are returned.

```
 $ curl https://api.xurrent.com/v1/sites
```

```
status: 200 OK
```

```
[{"created_at":"2016-03-10T02:04:15-06:00","id":13,"name":"Widget Data Center","sourceID":4,"updated_at":"2016-03-10T02:04:15-06:00"},"..."]
```

Using the `?fields=` parameter specific fields can be selected.
The `id` field is implicit and is always included in the results.

```
 $ curl https://api.xurrent.com/v1/sites?fields=name,country,disabled
```

```
status: 200 OK
```

```
[{"country":"US","disabled":false,"id":13,"name":"Widget Data Center"},"..."]
```

### Account

When the account of the resource is different from the account of the authenticated user,
the `account` [reference](../data_types.html#references) will be provided.

### Disabled

When a disabled resource is returned in a collection, the `disabled: true` property will be provided.
