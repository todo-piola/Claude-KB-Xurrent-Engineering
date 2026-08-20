# Survey Responses API

- [List survey responses](index.html#list-survey-responses)
- [Get a single survey response](index.html#get-a-single-survey-response)
- [Create a survey response](index.html#create-a-survey-response)
- [Update a survey response](index.html#update-a-survey-response)
- [Fields](index.html#fields)

## List survey responses

List all survey responses for an account:

```
GET /survey_responses
```

### Response

```
status: 200 OK
```

```
[{"id":187,"created_at":"2021-07-21T06:55:47-05:00","updated_at":"2021-07-21T06:55:47-05:00","survey":{"id":1,"name":"My Survey","nodeID":"..."},"service":{"id":31,"name":"Personal Computing","...":"..."},"year":2021,"month":7,"rating":null,"nodeID":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of survey responses.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of survey responses:

`id` `survey` `service` `year` `month` `rating` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `created_at` `updated_at` `responded_at` `survey`

### Sorting

By default a collection of survey responses is sorted **ascending** by `id`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `created_at` `updated_at`

## Get a single survey response

```
GET /survey_responses/:id
```

### Response

```
status: 200 OK
```

```
{"completed":true,"created_at":"2021-07-21T06:55:44-05:00","id":178,"rating":null,"rating_calculation_json":null,"responded_at":"2021-07-21T06:55:44-05:00","service":{"id":31,"name":"Personal Computing","...":"..."},"source":null,"sourceID":null,"survey":{"id":1,"name":"My Survey","nodeID":"..."},"updated_at":"2021-07-21T06:55:44-05:00","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Create a survey response

```
POST /survey_responses
```

When creating a new survey response [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created survey response and is similar to the response in [Get a single survey response](index.html#get-a-single-survey-response).

## Update a survey response

```
PATCH /survey_responses/:id
```

When updating an survey response [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created survey response and is similar to the response in [Get a single survey response](index.html#get-a-single-survey-response).

## Fields

completed
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The completed flag is used to indicate whether the user completed the survey.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the survey response was created.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the survey response.

rating
: *Optional* **[decimal](../general/data_types.html)** — Rating calculated based on the answers of this response.

rating\_calculation\_json
: *Readonly* **[string](../general/data_types.html)** — How the individual answers were combined to calculate the rating. (String can be parsed to JSON).

responded\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the user started the survey.

service
: *Required* **[reference](../general/data_types.html#references) to [Service](../services.html)** — Service this response is about.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

survey
: *Required* **[reference](../general/data_types.html#references) to [Survey](../surveys.html)** — Survey this response is for.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the survey response. If the survey response has no updates it contains the `created_at` value.
