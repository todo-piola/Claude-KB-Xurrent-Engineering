# Survey Responses - Survey Answers API

- [List all answers of a survey response](index.html#list-all-answers-of-a-survey-response)
- [Get a single answer of a survey response](index.html#get-a-single-answer-of-a-survey-response)
- [Add an answer to a survey response](index.html#add-an-answer-to-a-survey-response)
- [Update an answer of a survey response](index.html#update-an-answer-of-a-survey-response)
- [Remove an answer from a survey response](index.html#remove-an-answer-from-a-survey-response)
- [Remove all answers from a survey response](index.html#remove-all-answers-from-a-survey-response)
- [Fields](index.html#fields)

## List all answers of a survey response

List all answers of a survey response with a specific ID.

```
GET /survey_responses/:id/survey_answers
```

### Response

```
status: 200 OK
```

```
[{"id":21,"survey_response":{"id":182,"...":"..."},"survey_question":{"id":29,"question":"What could we do to improve?","nodeID":"..."},"text":"Serve coffee","rating":null,"created_at":"2021-07-21T06:55:45-05:00","updated_at":"2021-07-21T06:55:45-05:00","nodeID":"..."},{"id":22,"survey_response":{"id":182,"...":"..."},"survey_question":{"id":28,"question":"How do you rate us?","nodeID":"..."},"text":null,"rating":80,"created_at":"2021-07-21T06:55:50-05:00","updated_at":"2021-07-21T06:55:50-05:00","nodeID":"..."},"..."]
```

The response contains [these fields](index.html#collection-fields) by default.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of survey answers:

`id` `survey_response` `survey_question` `text` `rating` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../../general/field_selection/index.html#collection-of-resources).

## Get a single answer of a survey response

```
GET /survey_responses/:id/survey_answers/:answer_id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2022-09-15T08:34:14-05:00","id":154,"rating":null,"source":null,"sourceID":null,"survey_question":{"id":5,"question":"Rate us","localized_question":"Rate us","nodeID":"..."},"survey_response":{"id":54,"year":2022,"month":9,"survey":{"id":2,"name":"My Survey","nodeID":"..."},"service":{"id":31,"name":"Personal Computing","localized_name":"Personal Computing","nodeID":"...","provider":{"id":54,"name":"Widget Data Center, Internal IT","account":{"id":"widget","name":"Widget International"},"nodeID":"..."}},"nodeID":"..."},"text":"Yes please","updated_at":"2022-09-15T08:34:14-05:00","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Add an answer to a survey response

Add an answer to a survey response with a specific ID.

```
POST /survey_responses/:id/survey_answers
```

When creating a new answer for a survey [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"text":"Serve coffee!","...":"..."}
```

The response contains [all fields](index.html#fields) of the created answer and is similar to the response in [Get a single answer of a survey response](index.html#get-a-single-answer-of-a-survey-response).

## Update an answer of a survey response

Update an answer with a specific ID of a survey response with a specific ID.

```
PATCH /survey_responses/:id/survey_answers/:answer_id
```

When updating an existing answer of a survey response [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"text":"Serve coffee!","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated answer and is similar to the response in [Get a single answer of a survey response](index.html#get-a-single-answer-of-a-survey-response).

## Remove an answer from a survey response

Remove the link between a survey response with a specific ID and an answer with a specific ID.

```
DELETE /survey_responses/:id/survey_answers/:answer_id
```

### Response

```
status: 204 No Content
```

## Remove all answers from a survey response

Remove all answer links from a survey response with a specific ID.

```
DELETE /survey_responses/:id/survey_answers
```

### Response

```
status: 204 No Content
```

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the answer was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the answer.

rating
: *Optional* **[decimal](../../general/data_types.html)** — Only present for rating questions. The answer provided by the user.

source
: *Optional* **[string](../../general/data_types.html) (max 30)** - See [source](../../general/source.html)

sourceID
: *Optional* **[string](../../general/data_types.html) (max 128)** - See [source](../../general/source.html)

survey\_question
: *Required* **[reference](../../general/data_types.html#references) to [Question](../../surveys/survey_questions/index.html)** — Survey question this answer is for.

text
: *Optional* **[text](../../general/data_types.html) (max 64KB)** — Only present for text questions. The answer provided by the user.

text\_attachments
: *Writeonly* **[attachments](../../general/data_types.html#attachments)** The attachments used in the Text field.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the answer.
 If the answer has no updates it contains the `created_at` value.
