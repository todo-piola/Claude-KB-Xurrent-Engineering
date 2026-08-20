# Surveys - Survey Questions API

- [List all questions of a survey](index.html#list-all-questions-of-a-survey)
- [Get a single question of a survey](index.html#get-a-single-question-of-a-survey)
- [Add a question to a survey](index.html#add-a-question-to-a-survey)
- [Update a question of a survey](index.html#update-a-question-of-a-survey)
- [Remove a question from a survey](index.html#remove-a-question-from-a-survey)
- [Remove all questions from a survey](index.html#remove-all-questions-from-a-survey)
- [Fields](index.html#fields)

## List all questions of a survey

List all questions of a survey with a specific ID.

```
GET /surveys/:id/survey_questions
```

### Response

```
status: 200 OK
```

```
[{"id":2,"survey":{"id":1,"name":"My Survey","nodeID":"..."},"type":"text","question":"What could we do to improve?","position":1,"created_at":"2021-07-21T06:41:08-05:00","updated_at":"2021-07-21T06:41:08-05:00","...":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of survey questions:

`id` `survey` `type` `question` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../../general/field_selection/index.html#collection-of-resources).

## Get a single question of a survey

```
GET /surveys/:id/survey_questions/:question_id
```

### Response

```
status: 200 OK
```

```
{"id":2,"survey":{"id":1,"name":"My Survey","nodeID":"..."},"type":"text","question":"What could we do to improve?","position":1,"created_at":"2021-07-21T06:41:08-05:00","updated_at":"2021-07-21T06:41:08-05:00","...":"..."}
```

The response contains [these fields](index.html#fields).

## Add a question to a survey

Add a question to a survey with a specific ID.

```
POST /surveys/:id/survey_questions
```

When creating a new question for a survey [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"question":"How did we do?","...":"..."}
```

The response contains [all fields](index.html#fields) of the created survey and is similar to the response in [Get a single survey question](index.html#get-a-single-question-of-a-survey).

## Update a question of a survey

Update a question with a specific ID of a survey with a specific ID.

```
PATCH /surveys/:id/survey_questions/:question_id
```

When updating an existing question of a survey [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"question":"How did we do?","...":"..."}
```

The response contains [all fields](index.html#fields) of the created survey and is similar to the response in [Get a single survey question](index.html#get-a-single-question-of-a-survey).

## Remove a question from a survey

Remove question with a specific ID from a survey with a specific ID.

```
DELETE /surveys/:id/survey_questions/:question_id
```

### Response

```
status: 204 No Content
```

## Remove all questions from a survey

Remove all questions from a survey with a specific ID.

```
DELETE /surveys/:id/survey_questions
```

### Response

```
status: 204 No Content
```

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the question was created.

disabled
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — The Disabled box is checked when the question will not be shown to users completing the survey.

guidance
: *Optional* **[text](../../general/data_types.html) (max 64KB)** — The Guidance field is used for additional information to aid in answering the question.

guidance\_attachments
: *Writeonly* **[attachments](../../general/data_types.html#attachments)** The attachments used in the Guidance field.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the question.

position
: *Optional* **[integer](../../general/data_types.html)** — The Position field is used to specify the position of the question,
 relative to the other questions of the survey. The first question has position 1.

question
: *Required* **[string](../../general/data_types.html) (max 128)** — The question to pose to the user.

source
: *Optional* **[string](../../general/data_types.html) (max 30)** - See [source](../../general/source.html)

sourceID
: *Optional* **[string](../../general/data_types.html) (max 128)** - See [source](../../general/source.html)

type
: *Required* **[enum](../../general/enumerations/index.html)** — The Type field is used to select the type of the question. Valid values are:
: - `star_rating`: Star Rating
 - `text`: Free Text

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the question.
 If the question has no updates it contains the `created_at` value.

weight
: *Optional* **[integer](../../general/data_types.html)** — The Weight field is only used for rating question.
 It is used to specify the relative weight of the question compared to the others in the survey.
