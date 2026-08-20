# Contracts API

- [List contracts](index.html#list-contracts)
- [Get a single contract](index.html#get-a-single-contract)
- [Create a contract](index.html#create-a-contract)
- [Update a contract](index.html#update-a-contract)
- [Fields](index.html#fields)

## List contracts

List all contracts for an account:

```
GET /contracts
```

### Response

```
status: 200 OK
```

```
[{"id":84,"sourceID":null,"name":"0012PQ-MSAS-000605491 - Microsoft Software Assurance Support & Maintenance Agreement","status":"active","category":"support_and_maintenance_contract","created_at":"2016-03-13T02:10:15-05:00","supplier":{"id":27,"name":"Microsoft Corporation"},"updated_at":"2016-03-13T02:10:15-05:00"},{"id":87,"sourceID":null,"name":"0106-SAPUS-00046608 - SAP Enterprise Support for SAP ERP Central Component","status":"active","category":"support_and_maintenance_contract","created_at":"2016-03-13T02:10:15-05:00","supplier":{"id":29,"name":"SAP AG"},"updated_at":"2016-03-13T02:10:15-05:00"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of contracts.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/contracts/active`: List all active contracts
- `/contracts/inactive`: List all inactive contracts

### Collection Fields

By default the following fields will appear in collections of contracts:

`id` `sourceID` `name` `category` `status` `supplier` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `category` `status` `supplier` `created_at` `updated_at`

### Sorting

By default a collection of contracts is sorted **ascending** by `name`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `name` `category` `status` `supplier` `created_at` `updated_at`

## Get a single contract

```
GET /contracts/:id
```

### Response

```
status: 200 OK
```

```
{"category":"support_and_maintenance_contract","created_at":"2016-03-13T02:10:15-05:00","customer":{"id":5,"name":"Widget Data Center"},"customer_rep":{"id":63,"name":"Jo-Ann Stock"},"expiry_date":"2014-11-03","id":84,"name":"0012PQ-MSAS-000605491 - Microsoft Software Assurance Support & Maintenance Agreement","notice_date":"2014-10-04","remarks":"24x7 Problem Resolution Support=>\n- Support 24 hours a day, 7 days a week. You get around-the-clock phone support for business-critical issues. The number of phone incidents available depends on your Software Assurance investment.\n- Extended product support coverage. You get phone support for all Microsoft servers, Microsoft Windows operating systems, and Microsoft Office system products and editions, even if the specific license requiring support does not have Software Assurance coverage.\n- Unlimited online support. You get Web support during business hours for all Standard and Enterprise edition server products that are covered by Software Assurance.\n\nNew Version Rights=>\n- Access to new software versions that are released during the term of the Software Assurance coverage at no additional charge.\n- If a new version of a Microsoft product (e.g. any program within the Microsoft Office system) is released during the term of coverage, the licenses will automatically be upgraded to the new version. There is no need to go through the traditional procurement process.\n\nCharges=> For desktop software=> 29% of the license cost per annum.\nFor server software=> 25% of the license cost per annum.\nNo notice required.\nIf the annual support & maintenance charge is not paid, the support contract is not renewed.","source":null,"sourceID":null,"start_date":"2008-11-04","status":"active","supplier":{"id":27,"name":"Microsoft Corporation"},"supplier_contact":{"id":51,"name":"Barney Turban"},"time_zone":"Pacific Time (US & Canada)","updated_at":"2016-03-18T07:44:09-05:00","custom_fields":null,"ui_extension":null}
```

The response contains [these fields](index.html#fields).

## Create a contract

```
POST /contracts
```

When creating a new contract [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created contract and is similar to the response in [Get a single contract](index.html#get-a-single-contract)

## Update a contract

```
PATCH /contracts/:id
```

When updating a contract [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated contract and is similar to the response in [Get a single contract](index.html#get-a-single-contract)

## Fields

attachments
: *Readonly* **aggregated Attachments**

category
: *Required* **[enum](../general/enumerations/index.html)**, default: `lease_contract` — The Category field is used to select the appropriate category for the contract. Valid values are:
: - `lease_contract`: Lease Contract
 - `maintenance_contract`: Maintenance Contract
 - `support_contract`: Support Contract
 - `support_and_maintenance_contract`: Support & Maintenance Contract
 - `other_type_of_contract`: Other Type of Contract

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the contract was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the contract.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

customer
: *Required* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Customer field is used to select the [organization](../organizations.html) that pays for the contract.

customer\_rep
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The Customer representative field is used to select the [person](https://developer.xurrent.com/v1/persons/) who represents the customer of the contract.

expiry\_date
: *Optional* **[date](../general/data_types.html)** — The Expiry date field is used to specify the date through which the contract will be active. The contract expires at the end of this day if it is not renewed before then. When the contract has expired, its status will automatically be set to “Expired”.
: As long as notice still needs to be given to terminate the contract, the Expiry date field is to remain empty.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the contract.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the contract.
: If a unique ID is given to each contract, then this ID can be added at the start of the name. Example:
: - 2EGXQ2W – Dell 3-Year ProSupport and Next Business Day Onsite Repair for CMP00035

notice\_date
: *Optional* **[date](../general/data_types.html)** — The Notice date field is used to specify the last day on which the supplier organization can still be contacted to terminate the contract to ensure that it expires on the intended expiry date.
: The Notice date field is left empty, and the Expiry date field is filled out, when the contract is to expire on a specific date and no notice needs to be given to terminate it.
: As long as notice still needs to be given to terminate the contract, the Expiry date field is to remain empty.

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the contract that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Remarks field.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_date
: *Optional* **[date](../general/data_types.html)** — The Start date field is used to specify the first day during which the contract is active.

status
: *Required* **[enum](../general/enumerations/index.html)**, default: `scheduled_for_activation` — The Status field displays the current status of the contract. The available options are:
: - `being_prepared`: Being Prepared
 - `scheduled_for_activation`: Scheduled for Activation
 - `active`: Active
 - `expired`: Expired

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the organization that has provided the contract to the customer.

supplier\_contact
: *Optional* **[reference](../general/data_types.html#references) to
 [Person](../people.html)** — The Supplier contact field is used to select the person who represents the supplier of the contract.

time\_zone
: *Optional* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the start date, notice date and expiry date of the contract.

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the contract.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the contract. If the contract has no updates it contains the `created_at` value.
