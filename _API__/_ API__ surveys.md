# Surveys API

- [List surveys](../surveys.html#list-surveys)
- [Get a single survey](../surveys.html#get-a-single-survey)
- [Create a survey](../surveys.html#create-a-survey)
- [Update a survey](../surveys.html#update-a-survey)
- [Fields](../surveys.html#fields)

## List surveys

List all surveys for an account:

```
GET /surveys
```

### Response

```
status: 200 OK
```

```
[{"id":1,"name":"My Survey","created_at":"2021-07-21T06:41:06-05:00","updated_at":"2021-07-21T06:41:06-05:00","nodeID":"..."},"..."]
```

The response contains [these fields](../surveys.html#collection-fields) by default. [Filtering](../surveys.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of surveys.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/surveys/disabled`: List all disabled surveys
- `/surveys/enabled`: List all enabled surveys

### Collection Fields

By default the following [fields](../surveys.html#fields) will appear in collections of surveys:

`id` `name` `created_at` `updated_at`

Obtain a different set of [fields](../surveys.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../surveys.html#fields):

`id` `source` `sourceID` `created_at` `updated_at` `disabled` `name`

### Sorting

By default a collection of surveys is sorted **ascending** by `id`.

The following [fields](../surveys.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `created_at` `updated_at`

## Get a single survey

```
GET /surveys/:id
```

### Response

```
status: 200 OK
```

```
{"completion":null,"created_at":"2021-07-21T06:41:07-05:00","disabled":false,"id":12,"introduction":null,"name":"My Survey","source":null,"sourceID":null,"updated_at":"2021-07-21T06:41:07-05:00","...":"..."}
```

The response contains [these fields](../surveys.html#fields).

## Create a survey

```
POST /surveys
```

When creating a new survey [these fields](../surveys.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../surveys.html#fields) of the created survey and is similar to the response in [Get a single survey](../surveys.html#get-a-single-survey).

## Update a survey

```
PATCH /surveys/:id
```

When updating an survey [these fields](../surveys.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../surveys.html#fields) of the updated survey and is similar to the response in [Get a single survey](../surveys.html#get-a-single-survey).

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the survey was created.

completion
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Completion field is used to enter content shown to respondents on completion of the survey.

completion\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Completion field.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the survey may no longer be related to services and users should not be asked to use it to rate services it is linked to.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the survey.

introduction
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Introduction field is used to enter content shown to respondents before the first question of the survey.

introduction\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Introduction field.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the survey.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the survey. If the survey has no updates it contains the `created_at` value.
