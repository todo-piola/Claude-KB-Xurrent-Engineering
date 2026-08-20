# People API

**Tip**: If you are looking for information on how to integrate Active Directory or another LDAP system with Xurrent, please refer to the [Directory Services](../import/directory_services/index.html) page of the [Import API](../import.html).

- [List people](../people.html#list-people)
- [Get a single person](../people.html#get-a-single-person)
 - [Using a phone number to get a person](../people.html#using-a-phone-number-to-get-a-person)
- [Create a person](../people.html#create-a-person)
- [Update a person](../people.html#update-a-person)
- [Archive a person](../people.html#archive-a-person)
- [Trash a person](../people.html#trash-a-person)
- [Restore a person](../people.html#restore-a-person)
- [Fields](../people.html#fields)

## List people

List all people for an account and the related directory account:

```
GET /people
```

### Response

```
status: 200 OK
```

```
[{"name":"Ashok Kumar","created_at":"2016-03-14T03:09:55-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:31-06:00","manager":{"name":"Howard Tanner","id":5},"id":30,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},{"name":"Barney Turban","created_at":"2016-03-14T03:09:57-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:32-06:00","manager":{"name":"Howard Tanner","id":5},"id":58,"site":{"name":"Widget Data Center","id":13},"organization":{"name":"Widget Data Center, External IT","id":30},"disabled":false},"..."]
```

The response contains [these fields](../people.html#collection-fields) by default. [Filtering](../people.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of people.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/people/disabled`: List all disabled people
- `/people/enabled`: List all enabled people
- `/people/internal`: List all internal people
- `/people/directory`: List all people registered in the directory account of the support domain account from which the data is requested
- `/people/support_domain`: List all people registered in the account from which the data is requested (and *not* the related directory account)

### Collection Fields

By default the following [fields](../people.html#fields) will appear in collections of people:

`id` `sourceID` `name` `organization` `site` `manager` `created_at` `updated_at`

Obtain a different set of [fields](../people.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../people.html#fields):

`id` `source` `sourceID` `name` `disabled` `organization` `site` `manager` `created_at` `updated_at`
`employeeID` `primary_email` `supportID` `roles`

The filters on `primary_email` and `supportID` are not case sensitive.

The other string and text filters are case sensitive, *unless* they are used in combination with the `roles` filter.

### Sorting

By default a collection of people is sorted **ascending** by `name`.

The following [fields](../people.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `organization` `site` `manager` `created_at` `updated_at`

## Get a single person

```
GET /people/:id
```

### Response

```
status: 200 OK
```

```
{"picture_uri":null,"name":"Ashok Kumar","location":"Room 201, Desk 06","created_at":"2016-03-14T03:09:55-06:00","sourceID":null,"primary_email":"ashok.kumar@virtualsupport.com","job_title":"Trainee","addresses":[],"updated_at":"2016-03-14T03:10:31-06:00","manager":{"name":"Howard Tanner","id":5},"cost_per_hour":"80.0","information":"Temporarily working at the Widget Data Center to learn about network and system monitoring, before returning to India to provide first line support to Widget's IT users.","id":30,"time_format_24h":false,"site":{"name":"Widget Data Center","id":13},"time_zone":"Central Time (US & Canada)","organization":{"name":"Widget Data Center, External IT","id":30},"locale":"en-US","disabled":false,"vip":false,"work_hours":{"name":"Monday through Friday, 9:00am until 5:00pm"},"contacts":[{"label":"work","id":327,"telephone":"+1 (713) 987 2967"},{"label":"fax","id":326,"telephone":"+1 (713) 987 2911"}],"source":null,"supportID":null,"custom_fields":null,"ui_extension":null}
```

The response contains [these fields](../people.html#fields).

### Using a phone number to get a person

A person’s telephone number can also be used to retrieve the data of a person record.

```
GET /sd?telephone=1234567890
```

The [matching of telephone numbers](../cti/index.html#number-matching) works the same way as for the [Computer Telephony Integration (CTI)](../cti/index.html) interface.

The API user needs to have the Service Desk Analyst role of a Xurrent account to be able to use a telephone number to look up people records of that account.

When multiple person records contain the same telephone number (regardless of whether the `contact.label` is `work`, `mobile` or `home`), the data of all these person records will be retrieved, up to a maximum of 10 people.

## Create a person

If you are looking for information on how to integrate your Active Directory or LDAP systems with Xurrent please see the [Import API](../import.html).

```
POST /people
```

When creating a new person [these fields](../people.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"addresses":"...","...":"..."}
```

The response contains [all fields](../people.html#fields) of the created person and is similar to the response in [Get a single person](../people.html#get-a-single-person)

## Update a person

If you are looking for information on how to integrate your Active Directory or LDAP systems with Xurrent please see the [Import API](../import.html).

```
PATCH /people/:id
```

When updating a person [these fields](../people.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"addresses":"...","...":"..."}
```

The response contains [all fields](../people.html#fields) of the updated person and is similar to the response in [Get a single person](../people.html#get-a-single-person)

## Archive a person

```
POST /people/:id/archive
```

Moves a given person to the [Archive](../archive/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the person.

### Response

```
status: 200 OK
```

```
{"archived":"true","addresses":"...","...":"..."}
```

The response contains [all fields](../people.html#fields) of the archived person and is similar to the response in [Get a single person](../people.html#get-a-single-person)

## Trash a person

```
POST /people/:id/trash
```

Moves a given person to the [Trash](../trash/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the person.

### Response

```
status: 200 OK
```

```
{"trashed":"true","addresses":"...","...":"..."}
```

The response contains [all fields](../people.html#fields) of the trashed person and is similar to the response in [Get a single person](../people.html#get-a-single-person)

## Restore a person

```
POST /people/:id/restore
```

Moves a given person from the [Archive](../archive/index.html) or the [Trash](../trash/index.html) back into the active state.
This action requires the Account Administrator or Directory Administrator role in the account of the person.

### Response

```
status: 200 OK
```

```
{"addresses":"...","...":"..."}
```

The response contains [all fields](../people.html#fields) of the restored person and is similar to the response in [Get a single person](../people.html#get-a-single-person)

## Fields

addresses
: *Readonly* **aggregated [Addresses](addresses.html)** — The Address fields are used to enter the home and mailing addresses of the person.

attachments
: *Readonly* **aggregated Attachments**

authenticationID
: *Optional* **[string](../general/data_types.html) (max 128)** - The Authentication ID field may be used by the [Single Sign-On](../sso.html#authentication-id) feature to uniquely identify a user.

auto\_translation
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Auto translation box is checked when the person should be offered translations for texts that are written in languages other than the ones selected in the Language (locale) and the Do not translate (do\_not\_translate\_languages) fields. Such texts are translated automatically into the language selected in the Language (locale) field.

contacts
: *Readonly* **aggregated [Contacts](contacts.html)** — The Contact fields are used to enter the personal/work email addresses, fax/mobile/etc. of the person.

cost\_per\_hour
: *Optional* **[decimal](../general/data_types.html)** — The Cost per hour field is used to enter the person’s estimated total cost per work hour for the service provider organization. The value in this field should include the costs of the person’s salary (or rate in case of a long-term contractor), office space, service subscriptions, training, etc.

cost\_per\_hour\_currency
: *Optional* **[enum](../general/enumerations/index.html)** — The currency of the Cost per hour field value of the person. For valid values, see the list of currencies in the Currency field of the [Account API](../account.html).

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the person was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the person.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the person may no longer be related to other records.

do\_not\_translate\_languages
: *Optional* **[string](../general/data_types.html)** — The Do not translate field is used to select the languages that should not be translated automatically for the person. Translations will not be offered to the person for texts in any of these languages. This field can contain a comma-separated list of language codes. Supported language codes are: en, nl, de, fr, es, pt, it, da, fi, sv, pl, cs, tr, ru, ar, id, fa, no, zh, ja, ko, he, hi, ms.

employeeID
: *Optional* **[string](../general/data_types.html) (max 128)** - The Employee ID field is the unique identifier for a person typically based on order of hire or association with an organization.

exclude\_team\_notifications
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Indicates whether the person wants to receive team notifications.

guest
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — Indicates whether the person was registered as a guest in Self Service.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the person.

information
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Information field is used to add any additional information about the person that might prove useful.

information\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Information field.

job\_title
: *Optional* **[string](../general/data_types.html) (max 80)** — The Job title field is used to enter the person’s job title.

locale
: *Optional* **[string](../general/data_types.html) (max 5)** — The locale field has the label “Language” in the user interface. It is used to select the language preference of the person.

location
: *Optional* **[string](../general/data_types.html) (max 80)** — The Location field is used to enter the name or number of the room, cubicle or area where the person has his/her primary work space.

manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Manager field is used to select the manager or supervisor to whom the person reports.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the person’s name.

oauth\_person\_enablement
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — An enabled OAuth person is mentionable and visible in suggest fields, just like a real person.

organization
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Organization field is used to select the [Organization](../organizations.html) for which the person works as an employee or long-term contractor.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the person. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

primary\_email
: *Required* **[string](../general/data_types.html) (max 128)** — The Primary email field is used to enter the email address to which email notifications are to be sent. This email address acts as the unique identifier for the person within the Xurrent account. This primary email address also acts as the person’s login name if he/she is a user of the Xurrent service.

send\_email\_notifications
: *Optional* **[enum](../general/enumerations/index.html)** —
 Indicates when to send email notifications to the person. Valid values are:
: - `always`: Always
 - `when_offline`: Only when the person is offline
 - `never`: Never

show\_notification\_popup
: *Optional* **[enum](../general/enumerations/index.html)** —
 Indicates when to show a notification popup to the person. Valid values are:
: - `always`: Always, for all notifications
 - `important_only`: Only for important notifications
 - `never`: Never

site
: *Optional* **[reference](../general/data_types.html#references) to [Site](../sites.html)** — The Site field is used to select the [Site](../sites.html) where the person is stationed.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

supportID
: *Optional* **[string](../general/data_types.html) (max 50)** - The Support ID field is used to enter a number or code that a service desk analyst can ask the person for when the person contacts the service desk for support.

time\_format\_24h
: *Optional* **[boolean](../general/data_types.html)** - The Time format field is used to indicate whether the person prefers to see times displayed within the Xurrent service in the 24-hour format or not (in which case the 12-hour format is applied).

time\_zone
: *Optional* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone in which the person normally resides.

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the person.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the person. If the person has no updates it contains the `created_at` value.

vip
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The VIP box is checked to indicate that the person is a very important person.

work\_hours
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Work hours field is used to select a [Calendar](../calendars/index.html) that represents the work hours of the person.
