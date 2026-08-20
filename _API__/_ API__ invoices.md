# Invoices API

- [List invoices](../invoices.html#list-invoices)
- [Get a single invoice](../invoices.html#get-a-single-invoice)
- [Create a invoice](../invoices.html#create-a-invoice)
- [Update a invoice](../invoices.html#update-a-invoice)
- [Fields](../invoices.html#fields)

## List Invoices

List all invoices for an account:

```
GET /invoices
```

### Response

```
status: 200 OK
```

```
[{"id":351,"sourceID":null,"description":"HP ProLiant BL260c servers","invoice_nr":"36798292-A","invoice_date":"2017-11-19","amount":"7200.0","created_at":"2017-11-22T14:32:28-06:00","updated_at":"2017-11-22T14:33:06-06:00","project":{"id":7497,"subject":"Digital Operations Center (DOC)"}},{"id":396,"sourceID":null,"description":"APC NetShelter rack","invoice_nr":"170092403","invoice_date":"2017-11-20","amount":"1408.0","created_at":"2017-11-28T12:01:50-06:00","updated_at":"2017-11-28T12:01:50-06:00","project":{"id":7497,"subject":"Digital Operations Center (DOC)"}},"..."]
```

The response contains [these fields](../invoices.html#collection-fields) by default. [Filtering](../invoices.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of invoices.

### Collection Fields

By default the following fields will appear in collections of invoices:

`id` `sourceID` `description` `invoice_type` `invoice_nr` `invoice_date` `amount` `created_at` `updated_at`

Obtain a different set of [fields](../invoices.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../invoices.html#fields):

`id` `source` `sourceID` `description` `invoice_type` `po_nr` `invoice_nr` `invoice_date` `created_at` `updated_at`

### Sorting

By default a collection of invoices is sorted **descending** by `invoice_date`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `description` `invoice_nr` `invoice_date` `created_at` `updated_at`

## Get a Single Invoice

```
GET /invoices/:id
```

### Response

```
status: 200 OK
```

```
{"amount":"7200.0","attachments":[{"name":"HP 36798292-A.pdf","uri":"https://itrp.s3-accelerate.dualstack.amazonaws.com/...","inline":false,"size":520410}],"capital_expenditure":true,"created_at":"2017-11-22T14:32:28-06:00","description":"HP ProLiant BL260c servers","id":351,"invoice_date":"2017-11-19","invoice_nr":"36798292-A","po_nr":"PO33729-01","quantity":2,"remarks":"These are the 2 servers for the DOC project.","service":{"id":24,"name":"Service Management (ITRP)","localized_name":"Service Management (ITRP)","provider":{"id":45,"name":"Widget Data Center, External IT","account":{"id":"widget","name":"Widget International"}}},"source":"4me","sourceID":null,"supplier":{"id":32,"name":"HP"},"unit_price":"3600.0","updated_at":"2017-11-22T14:32:28-06:00","project":{"id":7497,"subject":"Digital Operations Center (DOC)"}}
```

The response contains [these fields](../invoices.html#fields).

## Create a Invoice

```
POST /invoices
```

When creating a new invoice [the fields listed below](../invoices.html#fields) are available.

*Please note* When creating an invoice, depending the type of invoice you want to create, you need to specify a value for exactly one of the following fields:

- `flsa_id`
- `sla_id`
- `contract_id`
- `project_id`
- `ci_ids`

Once an invoice is created its type can no longer be changed. When one of the first 4 fields above is used, the reference cannot be changed.
If the invoice is linked to [Configuration Items](../configuration_items/index.html) one can add and remove items later,
via the [nested configuration items endpoint](cis.html).

### Response

```
status: 201 Created
```

```
{"amount":"...","...":"..."}
```

The response contains [all fields](../invoices.html#fields) of the created invoice and is similar to the response in [Get a single invoice](../invoices.html#get-a-single-invoice)

## Update a Invoice

```
PATCH /invoices/:id
```

When updating a invoice [these fields](../invoices.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"amount":"...","...":"..."}
```

The response contains [all fields](../invoices.html#fields) of the updated invoice and is similar to the response in [Get a single invoice](../invoices.html#get-a-single-invoice)

## Fields

amount
: *Readonly* **[decimal](../general/data_types.html)** — The Amount field contains the product of the Unit price field value and the Quantity field value.

amortize
: *Optional* **[boolean](../general/data_types.html)** — Whether the invoice amount is to be amortized over time.

amortization\_start
: *Optional* **[datetime](../general/data_types.html)** — The start date of the period over which the invoice is to be amortized.

amortization\_end
: *Optional* **[datetime](../general/data_types.html)** — The end date of the period over which the invoice is to be amortized.

attachments
: *Readonly* **aggregated Attachments**

ci\_ids
: *Only supported on create* **array of [references](../general/data_types.html#references) to [Configuration Items](../configuration_items/index.html)** — The configuration items linked to be linked to the created invoice. Once the invoice has been created the linked
 configuration items can be managed via the [nested configuration items endpoint](cis.html).
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

contract
: *Readonly* **[reference](../general/data_types.html#references) to [Contract](../contracts/index.html)** — The contract linked to this invoice.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

currency
: *Optional* **[enum](../general/enumerations/index.html)** — The currency of the Amount field value of the invoice. For valid values, see the list of currencies in the Currency field of the [Account API](../account.html).

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the invoice was created.

depreciation\_method
: *Required* **[enum](../general/enumerations/index.html)** — Whether or not the invoice should be depreciated and if so, which depreciation method is to be applied. When creating a new invoice and a value is not specified for this field, and the invoice is related to a configuration item, the value is set to the depreciation method of the product of the configuration item.
 Valid values are:

 - `not_depreciated`: Not Depreciated
 - `double_declining_balance`: Double Declining Balance
 - `reducing_balance`: Reducing Balance (or Diminishing Value)
 - `straight_line`: Straight Line (or Prime Cost)
 - `sum_of_the_years_digits`: Sum of the Year’s Digits

depreciation\_start
: *Required* **[date](../general/data_types.html)** — The date on which to start depreciating the asset.

description
: *Required* **[string](../general/data_types.html) (max 220)** — The Description field is used to enter a short description of what was acquired.

financialID
: *Optional* **[string](../general/data_types.html) (max 128)** — The unique identifier by which the invoice is known in the financial system.

flsa
: *Readonly* **[reference](../general/data_types.html#references) to [First Line Support Agreement](../first_line_support_agreements/index.html)** — The first line support agreement linked to this invoice.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the invoice.

invoice\_date
: *Required* **[date](../general/data_types.html)** — The Invoice date field is used to specify the date on which the invoice was sent out by the supplier.

invoice\_nr
: *Required* **[string](../general/data_types.html) (max 128)** — The Invoice number field is used to enter the invoice number that the supplier specified on the invoice.

invoice\_type
: *Readonly* **[string](../general/data_types.html)** — The type of the record that is linked to the invoice. One of: `workflow`, `project`, `sla`, `flsa`, `cis`, `contract`

po\_nr
: *Optional* **[string](../general/data_types.html) (max 128)** — The PO number field is used to enter the number of the purchase order that was sent to supplier.

project
: *Readonly* **[reference](../general/data_types.html#references) to [Project](../projects/index.html)** — The Project linked to this invoice.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

quantity
: *Required* **[decimal](../general/data_types.html)**, default: `1` — The Quantity field is used to enter the number of units that were acquired.

rate
: *Optional* **[integer](../general/data_types.html)** — The Rate field is used to specify the yearly rate that should be applied to calculate the depreciation of the linked configuration items using the reducing balance (or diminishing value) method. When creating a new invoice and a value is not specified for this field, it is set to the rate of the product that the configuration items belong to.

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the contract that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Remarks field.

salvage\_value
: *Optional* **[decimal](../general/data_types.html)** — The value of this invoice at the end of its useful life (i.e. at the end of its depreciation period). When a value is not specified for this field, it is set to zero.

salvage\_value\_currency
: *Optional* **[enum](../general/enumerations/index.html)** — The currency of the Salvage value field value of the invoice. For valid values, see the list of currencies in the Currency field of the [Account API](../account.html).

sla
: *Readonly* **[reference](../general/data_types.html#references) to [Service Level Agreement](../service_level_agreements.html)** — The service level agreement linked to this invoice.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

service
: *Readonly* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is automatically set to the “service”:/help/service that is linked to the workflow, service level agreement, project or configuration item.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the organization from which the invoice was received.

unit\_price
: *Optional* **[decimal](../general/data_types.html)** — The Unit price field is used to enter the amount that the supplier has charged per unit that was acquired.

useful\_life
: *Optional* **[integer](../general/data_types.html)** — The Useful life field is used to enter the number of years within which the linked configuration items are to be depreciated. When creating a new invoice and a value is not specified for this field, it is set to the useful life of the product that the configuration items belong to.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the invoice. If the invoice has no updates it contains the `created_at` value.

workflow
: *Readonly* **[reference](../general/data_types.html#references) to [Workflow](../workflows.html)** — The workflow linked to this invoice.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).
