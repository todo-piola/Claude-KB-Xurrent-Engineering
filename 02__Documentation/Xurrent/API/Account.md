# Account API

- [Get an Account](../account.html#get-an-account)
- [Fields](../account.html#fields)

## Get an Account

```
GET /account
```

### Response

```
status: 200 OK
```

```
{"currency":"usd","locale":"en-US","name":"Widget North America - HR","organization":{"id":8621,"name":"Widget North America, Human Resources","account":{"id":"widget","name":"Widget International"}},"owner":{"id":660219,"name":"James Ballance","account":{"id":"widget","name":"Widget International"}},"plan":"premium_plus","start_of_week":"mon","time_zone":"Eastern Time (US & Canada)","time_format_24h":true,"url":"https://wna-hr.xurrent.com","id":"wna-hr","directory_account":{"id":"widget","name":"Widget International"},"strong_privacy":true}
```

The response contains [these fields](../account.html#fields).

## Fields

currency
: *Required* **[enum](../general/enumerations/index.html)** — The Currency field is used to select the currency that is applied to all financial values stored in the account. Valid values are:
: - `:aed`: United Arab Emirates Dirham
 - `:ars`: Argentine Peso
 - `:aud`: Australian Dollar
 - `:brl`: Brazilian Real
 - `:btc`: Bitcoin
 - `:cad`: Canadian Dollar
 - `:chf`: Swiss Franc
 - `:cny`: Chinese Yuan
 - `:cop`: Colombian Peso
 - `:czk`: Czech Republic Koruna
 - `:dkk`: Danish Krone
 - `:dzd`: Algerian Dinar
 - `:eur`: Euro
 - `:gbp`: British Pound
 - `:hkd`: Hong Kong Dollar
 - `:hrk`: Croatian Kuna
 - `:huf`: Hungarian Forint
 - `:idr`: Indonesian Rupiah
 - `:ils`: Israeli Shekel
 - `:inr`: Indian Rupee
 - `:jpy`: Japanese Yen
 - `:krw`: Korean Won
 - `:mxn`: Mexican Peso
 - `:ngn`: Nigerian Naira
 - `:nok`: Norwegian Krone
 - `:nzd`: New Zealand Dollar
 - `:omr`: Omani Rial
 - `:pkr`: Pakistani Rupee
 - `:php`: Philippine Peso
 - `:pln`: Polish Zloty
 - `:rub`: Russian Rouble
 - `:sek`: Swedish Krona
 - `:sgd`: Singapore Dollar
 - `:thb`: Thai Baht
 - `:try`: Turkish Lira
 - `:twd`: Taiwan Dollar
 - `:usd`: United States Dollar
 - `:zar`: South African Rand

directory\_account
: *Readonly* **[reference](../general/data_types.html#references) to [Account](../account.html)** — The Directory account field contains a value only for support domain accounts.

id
: *Readonly* **[string](../general/data_types.html)** — The unique ID of the account.

locale
: *Required* **[enum](../general/enumerations/index.html)** — The Language field is used to select the language in which the records of the account are stored. It is also the default language that is applied to new Person records.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the full name of the account.

organization
: *Readonly* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Organization field is set to the organization for which the account was prepared.

owner
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Owner field is used to select the account administrator who is allowed to update the billing information and settings of the account.

plan
: *Required* **[enum](../general/enumerations/index.html)** — The Plan field is used to select the Plan for the account. Valid values are:
: - `basic`
 - `premium`
 - `premium_plus`

strong\_privacy
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Strong privacy box is checked when access to requests, problems and tasks needs to be restricted to members of the teams to which they are assigned.

time\_format\_24h
: *Optional* **[boolean](../general/data_types.html)**, default: `true` — The Time format field is the default format for displaying time values that is applied to new Person records. When `true`, times are displayed within the Xurrent service in the 24-hour format, otherwise the 12-hour format is applied.

time\_zone
: *Required* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the account’s analytics and report data. It is also the default time zone that is applied to new Person records.

url
: *Readonly* **[string](../general/data_types.html) (max 50)** — The Account URL field contains the web address that is used to access the account.
