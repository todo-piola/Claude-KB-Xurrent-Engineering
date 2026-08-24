# Skill Pools API

- [List skill pools](index.html#list-skill-pool)
- [Get a single skill pool](index.html#get-a-single-skill-pool)
- [Create a skill pool](index.html#create-a-skill-pool)
- [Update a skill pool](index.html#update-a-skill-pool)
- [Fields](index.html#fields)

## List skill pools

List all skill pools for an account:

```
GET /skill_pools
```

### Response

```
status: 200 OK
```

```
[{"name":"Chief Financial Controllers","created_at":"2016-03-14T03:10:36-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:36-06:00","id":7,"disabled":false},{"name":"Expense Reporting SMEs","created_at":"2016-03-14T03:10:36-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:36-06:00","id":8,"disabled":false},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of skill pools.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/skill_pools/disabled`: List all disabled skill pools
- `/skill_pools/enabled`: List all enabled skill pools

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of skill pools:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `disabled` `created_at` `updated_at`

### Sorting

By default a collection of skill pools is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single skill pool

```
GET /skill_pools/:id
```

### Response

```
status: 200 OK
```

```
{"picture_uri":null,"name":"Chief Financial Controllers","remarks":"All large projects must be approved by at least 1 chief financial controller","created_at":"2016-03-14T03:10:36-06:00","source":null,"sourceID":null,"cost_per_hour":"250.00","updated_at":"2016-03-14T03:10:36-06:00","manager":{"name":"Rodney Wilson","id":34},"id":7,"disabled":false}
```

The response contains [these fields](index.html#fields).

## Create a skill pool

```
POST /skill_pools
```

When creating a new skill pool [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created skill pool and is similar to the response in [Get a single skill pool](index.html#get-a-single-skill-pool).

## Update a skill pool

```
PATCH /skill_pools/:id
```

When updating a skill pool [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated skill pool and is similar to the response in [Get a single skill pool](index.html#get-a-single-skill-pool).

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the skill pool was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the skill pool may no longer be related to other records.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the skill pool.

manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field is used to select the manager or supervisor of the skill pool. This person is able to maintain the information about the skill pool. The manager of a skill pool does not need to be a member of the skill pool.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the skill pool.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the skill pool. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the skill pool that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Remarks field.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the skill pool. If the skill pool has no updates it contains the `created_at` value.

cost\_per\_hour
: *Optional* **[decimal](../general/data_types.html)** — The Cost per hour field is used to enter the skill pool’s estimated total cost per work hour for the service provider organization.

cost\_per\_hour\_currency
: *Optional* **[enum](../general/enumerations/index.html)** — The currency of the Cost per hour field value of the skill pool. For valid values, see the list of currencies in the Currency field of the [Account API](../account.html).
