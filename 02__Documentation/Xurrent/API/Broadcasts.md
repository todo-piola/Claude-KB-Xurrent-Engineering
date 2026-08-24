# Broadcasts API

- [List broadcasts](../broadcasts.html#list-broadcasts)
- [Get a single broadcast](../broadcasts.html#get-a-single-broadcast)
- [Create a broadcast](../broadcasts.html#create-a-broadcast)
- [Update a broadcast](../broadcasts.html#update-a-broadcast)
- [Fields](../broadcasts.html#fields)

## List broadcasts

List all broadcasts for an account:

```
GET /broadcasts
```

### Response

```
status: 200 OK
```

```
[{"id":349,"sourceID":null,"created_at":"2016-05-23T06:06:34-05:00","updated_at":"2016-05-23T06:06:45-05:00"},{"id":321,"sourceID":null,"created_at":"2016-05-22T03:20:36-05:00","updated_at":"2016-05-23T04:30:01-05:00"},"..."]
```

The response contains [these fields](../broadcasts.html#collection-fields) by default. [Filtering](../broadcasts.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of broadcasts.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/broadcasts/active`: List all active broadcasts
- `/broadcasts/inactive`: List all inactive broadcasts

### Collection Fields

By default the following [fields](../broadcasts.html#fields) will appear in collections of broadcasts:

`id` `sourceID` `created_at` `updated_at`

Obtain a different set of [fields](../broadcasts.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../broadcasts.html#fields):

`id` `sourceID` `created_at` `updated_at` `start_at` `end_at` `message_type`

The filter on `sourceID` is not case sensitive.

### Sorting

By default a collection of broadcasts is sorted **descending** by `start_at`.

The following [fields](../broadcasts.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `start_at` `end_at` `created_at` `updated_at`

## Get a single broadcast

```
GET /broadcasts/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2016-05-22T03:20:36-05:00","disabled":false,"end_at":null,"id":1,"message":"<p>Foo</p>","message_type":"warning","service_instances":[{"id":33,"name":"Amsterdam Network","localized_name":"Amsterdam Network"},"..."],"source":"4me","sourceID":null,"start_at":"2014-05-22T08:20:00Z","teams":[],"time_zone":"Central Time (US & Canada)","translations":[{"id":321,"locale":"en-US"},"..."],"updated_at":"2014-05-23T04:30:01-05:00","visibility":"covered_for"}
```

The response contains [these fields](../broadcasts.html#fields).

## Create a broadcast

```
POST /broadcasts
```

When creating a new broadcast [these fields](../broadcasts.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"message":"...","...":"..."}
```

The response contains [all fields](../broadcasts.html#fields) of the created broadcast and is similar to the response in [Get a single broadcast](../broadcasts.html#get-a-single-broadcast)

## Update a broadcast

```
PATCH /broadcasts/:id
```

When updating a broadcast [these fields](../broadcasts.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"message":"...","...":"..."}
```

The response contains [all fields](../broadcasts.html#fields) of the updated broadcast and is similar to the response in [Get a single broadcast](../broadcasts.html#get-a-single-broadcast)

## Fields

customers
: *Optional* **array of [references](../general/data_types.html#references) to [Organization](../organizations.html)** — The Customers field is used to select one or more customer organizations when the broadcast is to be displayed for the specialists of the account in requests that were received from the selected organizations. This field is available only when the “Specialists in requests from the following customers” visibility option is selected.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the broadcast was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the message should not be broadcasted.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the broadcast.

end\_at
: *Optional* **[datetime](../general/data_types.html)** — The End field is used to select the end date and time of the broadcast. This field is left empty when the message is to be broadcasted until the Disabled box is checked.
: If the broadcast should end at midnight at the end of a day, specify 12:00am or 24:00.

message
: *Required* **[text](../general/data_types.html) (max 64KB)** — The Message field is used to enter the information that is to be broadcasted.

message\_type
: *Required* **[enum](../general/enumerations/index.html)** — The Message type field is used to select the appropriate icon for the message. The selected icon is displayed alongside the message when the broadcast is presented. Valid values are:
: - `outage`: Outage
 - `available`: Available
 - `warning`: Warning
 - `info`: Information

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the broadcast that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Remarks field.

organizations
: *Optional* **array of [references](../general/data_types.html#references) to [Organization](../organizations.html)** — The Organization table field is used to select the organizations, to which people belong, that need to see the broadcast.

request
: *Optional* **[reference](../general/data_types.html#references) to [Request](../requests.html)** — The Request group field is used to select the request group to which end users can subscribe when they are also affected by the issue for which the broadcast was created.

source
: *Optional* **[string](../general/data_types.html) (max 30)** — See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** — See [source](../general/source.html)
: The message will be stored/displayed as the translation for the locale of the account.

service\_instances
: *Optional* **array of [references](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The Service instances table field is used to select the service instances for which the people, who are covered for them by an active SLA, need to see the broadcast. This table field is available only when the “People covered for the following service instance(s)” visibility option is selected.

sites
: *Optional* **array of [references](../general/data_types.html#references) to [Site](../sites.html)** — The Sites table field is used to select the sites for which people need to see the broadcast.

skill\_pools
: *Optional* **array of [references](../general/data_types.html#references) to [Skill Pool](../skill_pools/index.html)** — The Organization table field is used to select the skill pools, to which people belong, that need to see the broadcast.

start\_at
: *Required* **[datetime](../general/data_types.html)**, default: the current date and time in the timezone of the user — The Start field is used to specify the start date and time of the broadcast.
: If the broadcast should start at midnight at the start of a day, specify 00:00.

teams
: *Optional* **array of [references](../general/data_types.html#references) to [Team](../teams.html)** — The Teams table field is used to select the teams which members need to see the broadcast. This table field is available only when the “Members of the following team(s)” visibility option is selected.

time\_zone
: *Required* **[time\_zone](../general/data_types.html)**, default: the time zone of the account user — The Time zone field is used to select the time zone that applies to the dates and times specified in the Start and End fields.

translations
: *Optional* **array of [references](../general/data_types.html#references) to [Broadcast Translations](translations/index.html)**

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the broadcast. If the broadcast has no updates it contains the `created_at` value.

visibility
: *Required* **[enum](../general/enumerations/index.html)**, default: `all_of_account` — The Visible for options are used to define the target audience of the broadcast. Valid values are:
: - `all_of_account`: All people of the account
 - `account_specialists`: All specialists of the account
 - `covered_for_any`: People covered for any of the service instances of the account
 - `covered_for`: People covered for the following service instance(s)
 - `customers`: Specialists in requests from the following customers
 - `members_of_skill_pools`: Members of the following skill pool(s)
 - `members_of_teams`: Members of the following team(s)
 - `organizations_and_descendants`: People of the following organization(s) and their descendants
 - `organizations`: People of the following organization(s)
 - `sites`: People of the following site(s)
