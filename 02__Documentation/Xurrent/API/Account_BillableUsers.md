# Account - Billable Users API

- [List billable users](index.html#list-billable-users)
- [Fields](index.html#fields)

## List Billable Users

List all current billable users of an account:

```
GET /account/billable_users
```

### Response

```
status: 200 OK
```

```
[{"id":552,"primary_email":"abbie.lindt@microsoft.com","name":"Abbie Lindt","organization":"Microsoft Corporation","business_unit":null,"sign_ins":0,"last_visit":null,"updates":0},{"id":70,"primary_email":"ashok.kumar@virtualsupport.com","name":"Ashok Kumar","organization":"Widget Data Center, External IT","business_unit":"Widget Data Center","sign_ins":14,"last_visit":"2015-10-30T15:22:25-05:00","updates":78},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../../general/pagination.html) are available to reduce/limit the collection of usage statements.

### Filtering

[Filtering](../../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `year` `month`

To obtain all billable users of an account for a previous month (e.g. October 2015):

```
GET /account/billable_users?year=2015&month=10
```

To retrieve the same billable users as a list of comma-separated values (CSV):

```
GET /account/billable_users.csv?year=2015&month=10
```

## Fields

account
: *Readonly* **[reference](../../general/data_types.html#references) to [Account](../../account.html)** — The account of the person.

business\_unit
: *Readonly* **[string](../../general/data_types.html) (max 128)** — The Business unit field shows the name of the business unit that the person’s organization belongs to.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the person.

last\_visit
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the person last accessed the Xurrent service.

name
: *Readonly* **[string](../../general/data_types.html) (max 128)** — The Name field is used to enter the person’s name.

organization
: *Readonly* **[string](../../general/data_types.html) (max 128)** — The Organization field shows the name of the organization that the person belongs to.

primary\_email
: *Readonly* **[string](../../general/data_types.html) (max 128)** — The Primary email field is used to enter the email address to which email notifications are to be sent. This email address acts as the unique identifier for the person within the Xurrent account. This primary email address also acts as the person’s login name if he/she is a user of the Xurrent service.

region
: *Readonly* **[string](../../general/data_types.html) (max 128)** — The Region field shows the name of the region of the person’s organization.

sign\_ins
: *Readonly* **[integer](../../general/data_types.html)** — The total number of times to date that the person has signed into the Xurrent service.

updates
: *Readonly* **[integer](../../general/data_types.html)** — The number of record updates the person made in the given month through using the UI acting to support.
