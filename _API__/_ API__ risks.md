# Risks API

- [List risks](../risks.html#list-risk)
- [Get a single risk](../risks.html#get-a-single-risk)
- [Create a risk](../risks.html#create-a-risk)
- [Update a risk](../risks.html#update-a-risk)
- [Fields](../risks.html#fields)

## List risks

List all risks for an account:

```
GET /risks
```

### Response

```
status: 200 OK
```

```
[{"id":12348,"sourceID":null,"subject":"Integration with cloud application could lead to breach of our Data Protection Policy","severity":"high","status":"closed","closed_at":"2020-01-15T09:55:00-06:00","closure_reason":"transferred","created_at":"2020-01-10T07:36:00-06:00","updated_at":"2020-02-11T05:30:55-06:00"},"..."]
```

The response contains [these fields](../risks.html#collection-fields) by default. [Filtering](../risks.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of risks.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/risks/open`: List all open risks
- `/risks/closed`: List all closed risks

### Collection Fields

By default the following [fields](../risks.html#fields) will appear in collections of risks:

`id` `sourceID` `subject` `severity` `status` `mitigation_target_at` `closed_at` `closure_reason` `created_at` `updated_at`

Obtain a different set of [fields](../risks.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../risks.html#fields):

`id` `source` `sourceID` `subject` `status` `mitigation_target_at` `closed_at` `created_at` `updated_at`

### Sorting

By default a collection of risks is sorted **ascending** by `name`.

The following [fields](../risks.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `mitigation_target_at` `closed_at` `created_at` `updated_at`

## Get a single risk

```
GET /risks/:id
```

### Response

```
status: 200 OK
```

```
{"closed_at":"2020-01-15T09:55:00-06:00","closure_reason":"transferred","created_at":"2020-01-10T07:36:00-06:00","custom_data":"{\"likelihood\":\"high\",\"impact\":\"high\",\"residual_risk\":\"high\"}","custom_fields":[{"id":"likelihood","value":"high"},{"id":"impact","value":"high"},{"id":"residual_risk","value":"high"}],"id":12348,"manager":{"id":6,"name":"Howard Tanner"},"severity":"high","source":"4me","sourceID":null,"status":"closed","subject":"Integration with cloud application could lead to breach of our Data Protection Policy","ui_extension":{"id":4,"name":"Risk","category":"risk","title":"Risk Assessment","account":{"id":"wdc","name":"Widget Data Center"},"localized_title":"Risk Assessment"},"updated_at":"2020-02-11T05:30:55-06:00","account":{"id":"wdc","name":"Widget Data Center"}}
```

The response contains [these fields](../risks.html#fields).

## Create a risk

```
POST /risks
```

When creating a new risk [these fields](../risks.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../risks.html#fields) of the created risk and is similar to the response in [Get a single risk](../risks.html#get-a-single-risk).

## Update a risk

```
PATCH /risks/:id
```

When updating a risk [these fields](../risks.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../risks.html#fields) of the updated risk and is similar to the response in [Get a single risk](../risks.html#get-a-single-risk).

## Fields

attachments
: *Readonly* **aggregated Attachments**
: Use [Risks - Notes API](notes/index.html) to get note attachments.

closed\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Closed at field is automatically set to the date and time at which the risk is saved with the status “Closed”.

closure\_reason
: *Optional* **[enum](../general/enumerations/index.html)** — The Closure reason field is used to select the appropriate closure reason for the risk when it has been closed. Valid values are:
: - `eliminated`: Eliminated - Risk Completely Eliminated
 - `accepted`: Accepted - Risk Level Accepted
 - `mitigated`: Mitigated - Risk Reduced to Acceptable Level
 - `transferred`: Transferred - Risk Transferred to Another Organization
 - `no_risk`: No Risk - Assessment Found No Risk

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the risk was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the risk.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the risk.

manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field is used to select the manager of the risk. This person is able to maintain the information about the risk.

mitigation\_target\_at
: *Optional* **[date](../general/data_types.html)** — The date by which the risk should have been mitigated.

note
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Note field is used to provide a detailed description of the risk and the actions that are planned or have already been taken to eliminate it, or to minimize its severity. This field is also used when the status is set to ‘Closed’ to explain why it was decided to close the risk.
: The Note field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

note\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Note field.

resolution\_duration
: *Readonly* **[integer](../general/data_types.html)** — The number of minutes it took to complete this risk, which is calculated as the difference between the `created_at` and `closed_at` values.

severity
: *Optional* **[enum](../general/enumerations/index.html)** with `reference` field of [Risk Severity](../risk_severities/index.html) — The Severity field is used to select the severity of the risk.

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `anticipated` — The Status field is used to select the current status of the risk. Valid values are:
: - `anticipated`: Anticipated
: - `materialized`: Materialized
: - `closed`: Closed

subject
: *Required* **[string](../general/data_types.html) (max 128)** — The Subject field is used to enter the subject of the risk.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the risk.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the risk. If the risk has no updates it contains the `created_at` value.
