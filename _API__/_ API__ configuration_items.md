# Configuration Items API

**Note** If you are looking for information on how to integrate a discovery tool with Xurrent, please refer to the [Discovery Tools](../import/discovery_tools/index.html) page of the [Import API](../import.html).

- [List configuration items](index.html#list-configuration-items)
- [Get a single configuration item](index.html#get-a-single-configuration-item)
- [Create a configuration item](index.html#create-a-configuration-item)
- [Update a configuration item](index.html#update-a-configuration-item)
- [Archive a configuration item](index.html#archive-a-configuration-item)
- [Trash a configuration item](index.html#trash-a-configuration-item)
- [Restore a configuration item](index.html#restore-a-configuration-item)
- [Fields](index.html#fields)

## List configuration items

List all configuration items for an account:

```
GET /cis
```

### Response

```
status: 200 OK
```

```
[{"name":"Adobe Reader 9.1.0","label":"Adobe Reader 9.1.0","created_at":"2016-03-14T03:11:22-06:00","sourceID":null,"updated_at":"2016-03-14T03:11:22-06:00","service":{"name":"Personal Computing","id":22,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"support_team":{"name":"End-User Support, Houston","id":9},"id":711,"product":{"name":"Adobe Reader","brand":"Adobe","category":"software/browser_viewer_application","id":33},"status":"in_production","software":true,"rule_set":"software"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of configuration items.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/cis/active`: List all active configuration items
- `/cis/inactive`: List all inactive configuration items
- `/cis/supported_by_my_teams`: List all configuration items which support team is one of the teams that the API user is a member of

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of configuration items:

`id` `sourceID` `software` `label` `name` `status` `product` `rule_set` `support_team` `service` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `label` `name` `status` `rule_set` `support_team` `created_at` `updated_at`
`product` `service` `systemID` `assetID` `serial_nr` `site` `financial_owner`

The filters on `label` and `serial_nr` are not case sensitive.

### Sorting

By default a collection of configuration items is sorted **ascending** by `label`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `label` `name` `status` `support_team` `created_at` `updated_at`

### Response

The response is similar to the response in [List configuration items](index.html#list-configuration-items)

## Get a single configuration item

```
GET /cis/:id
```

### Response

```
status: 200 OK
```

```
{"in_use_since":null,"site_license":null,"name":"Adobe Reader 9.1.0","label":"Adobe Reader 9.1.0","rule_set":"software","financial_owner":null,"assetID":null,"remarks":"No license required.","location":"Room 202, Software Safe","created_at":"2016-03-14T03:11:22-06:00","sourceID":null,"nr_of_licenses":null,"license_type":null,"updated_at":"2016-03-14T03:11:22-06:00","systemID":null,"supplier":null,"service":{"name":"Personal Computing","id":22,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"support_team":{"name":"End-User Support, Houston","id":9},"serial_nr":null,"rate":null,"po_nr":null,"warranty_expiry_date":null,"useful_life":null,"salvage_value":null,"id":711,"product":{"name":"Adobe Reader","brand":"Adobe","category":"software/browser_viewer_application","id":33},"license_expiry_date":null,"site":{"name":"Widget Data Center","id":13},"nr_of_processors":null,"temporary_license":null,"purchase_value":null,"status":"in_production","source":null,"software":true,"nr_of_cores":null,"depreciation_method":null,"custom_fields":null}
```

The response contains [these fields](index.html#fields).

## Create a configuration item

```
POST /cis
```

When creating a new configuration item [these fields](index.html#fields) are available.

**Important**: To facilitate integrations with discovery tools, the POST is treated as a PATCH in case the provided `name` or `label` is already used by an inactive CI in the same account.

### Response

```
status: 201 Created
```

```
{"assetID":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created configuration item and is similar to the response in [Get a single configuration item](index.html#get-a-single-configuration-item)

## Update a configuration item

```
PATCH /cis/:id
```

When updating a configuration item [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"assetID":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated configuration item and is similar to the response in [Get a single configuration item](index.html#get-a-single-configuration-item)

## Archive a configuration item

```
POST /cis/:id/archive
```

Moves a given configuration item to the [Archive](../archive/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the configuration item.

### Response

```
status: 200 OK
```

```
{"assetID":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the archived configuration item and is similar to the response in [Get a single configuration item](index.html#get-a-single-configuration-item)

## Trash a configuration item

```
POST /cis/:id/trash
```

Moves a given configuration item to the [Trash](../trash/index.html).
This action requires the Account Administrator or Directory Administrator role in the account of the configuration item.

### Response

```
status: 200 OK
```

```
{"assetID":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the trashed configuration item and is similar to the response in [Get a single configuration item](index.html#get-a-single-configuration-item)

## Restore a configuration item

```
POST /cis/:id/restore
```

Moves a given configuration item from the [Archive](../archive/index.html) or the [Trash](../trash/index.html) back into the view of “Inactive CIs”.
This action requires the Account Administrator or Directory Administrator role in the account of the configuration item.

### Response

```
status: 200 OK
```

```
{"assetID":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the restored configuration item and is similar to the response in [Get a single configuration item](index.html#get-a-single-configuration-item)

## Fields

alternate\_names
: *Optional* array of **[strings](../general/data_types.html)** — Alternate names a software configuration item is also known by.

assetID
: *Optional* **[string](../general/data_types.html) (max 50)**

attachments
: *Readonly* **aggregated Attachments**

ci\_type
: *Readonly* **[enum](../general/enumerations/index.html)** — Valid values are:
: - `software_version`: Software Version
 - `software_license_certificate`: Software License Certificate
 - `hardware`: Hardware
: Deprecated - The `ci_type` field is being phased out. Use the `rule_set` field instead.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the configuration item was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the related product.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

end\_of\_support\_date
: *Optional* **[date](../general/data_types.html)** — The End of support date field is used to specify the date on which support for the configuration item ends. It is typically populated through discovery or the GraphQL API rather than entered by hand.

financial\_owner
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Financial owner field is used to select the internal organization which budget is used to pay for the configuration item. If the CI is leased or rented, the organization that pays the lease or rent is selected in this field. When creating a new CI and a value is not specified for this field, it is set to the financial owner of the CI’s product.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the configuration item.

in\_use\_since
: *Optional* **[date](../general/data_types.html)** — The In use since field is used to specify the date on which the expense for the configuration item (CI) was incurred or, if the CI is depreciated over time, the date on which the depreciation was started. This is typically the invoice date.

label
: *Optional* **[string](../general/data_types.html) (max 160)** — The Label field is used to specify the label that is attached to the configuration item (CI). A label is automatically generated using the same prefix of other CIs of the same product category, followed by the next available number as the suffix.

last\_seen\_at
: *Optional* **[datetime](../general/data_types.html)** — The Last seen field is used to record the date and time at which the configuration item was most recently detected. It is typically populated through discovery or the GraphQL API rather than entered by hand.

license\_expiry\_date
: *Optional* **[date](../general/data_types.html)** — The License expiry date field is used to specify the date through which the temporary software license certificate is valid. The license certificate expires at the end of this day.

license\_type
: *Optional* **[enum](../general/enumerations/index.html)** — The License type field is used to select the type of license that the license certificate covers. Valid values are:
: - `concurrent_user_license`: Concurrent User License
 - `cpu_license`: CPU License
 - `installed_user_license`: Installed User License
 - `named_user_license`: Named User License
 - `unlimited_user_license`: Unlimited User License
 - `other_type_of_license`: Other Type of License

location
: *Optional* **[string](../general/data_types.html) (max 128)** — The Location field is used to enter the name or number of the room in which the CI is located, if it concerns a hardware CI.

location\_hint
: *Optional* **[string](../general/data_types.html) (max 2,048)** — A free-format “as discovered” physical-location string from the source protocol (for example SNMP `sysLocation`, a vCenter folder path, or an AWS tag), stored verbatim for reference. Use the `location` field for authoritative Site assignment.

name
: *Optional* **[string](../general/data_types.html) (max 160)** — The Name field is used to enter the name of the configuration item (CI). When creating a new CI and a value is not specified for this field, it is set to the name of the CI’s product.

nr\_of\_cores
: *Optional* **[integer](../general/data_types.html)** — The Nr. of cores field is used to enter the total number of processor cores that are installed in the server.

nr\_of\_licenses
: *Optional* **[integer](../general/data_types.html)** — The Nr. of licenses field is used to enter the number of licenses that the license certificate covers.

nr\_of\_processors
: *Optional* **[integer](../general/data_types.html)** — The Nr. of processors field is used to enter the number of processors that are installed in the server.

product
: *Required* **[reference](../general/data_types.html#references) to [Product](../products.html)** — The Product field can be used to relate the configuration item to a different product.

recurrence
: *Optional* **aggregated** — The recurrence settings hash, missing in case the configuration item has no recurrency defined. See [Recurrence](../recurrences.html) for the fields in the recurrence hash.

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the configuration item that might prove useful. When creating a new CI and a value is not specified for this field, it is set to the remarks of the CI’s product.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Remarks field.

rule\_set
: *Readonly* **[enum](../general/data_types.html)** — The Rule set field is automatically set to the rule set of the related product’s product category, except when the CI is a license certificate, in which case the rule set is `license_certificate`. Valid values are:
: - `license_certificate`: License Certificate
 - `logical_asset_with_financial_data`: Logical Asset with Financial Data
 - `logical_asset_without_financial_data`: Logical Asset without Financial Data
 - `physical_asset`: Physical Asset
 - `server`: Server
 - `software`: Software
 - `software_distribution_package`: Software Distribution Package

serial\_nr
: *Optional* **[string](../general/data_types.html) (max 50)** — The concatenation of Product Brand and Serial Number must be unique within a Xurrent account.

service
: *Optional* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the [Service](https://developer.xurrent.com/v1/service,s/) which service instance(s) the configuration item is, or will be, a part of. When creating a new CI and a value is not specified for this field, it is set to the service of the CI’s product.

site
: *Optional* **[reference](../general/data_types.html#references) to [Site](../sites.html)** — The Site field is used to select the [Site](../sites.html) at which the CI is located, if it concerns a hardware CI.

site\_license
: *Optional* **[boolean](../general/data_types.html)** — The Site license box is checked for license certificates that may only be used at one or more specific locations.

software
: *Readonly* **[boolean](../general/data_types.html)**, default: `false`
: Deprecated - The `software` field is being phased out. Use the `rule_set` field instead.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

status
: *Required* **[enum](../general/enumerations/index.html)** — The Status field is used to select the appropriate status for the configuration item (CI). Valid values are:
: - `ordered`: Ordered
 - `being_built`: Being Built
 - `in_stock`: In Stock
 - `reserved`: Reserved
 - `in_transit`: In Transit
 - `installed`: Installed
 - `being_tested`: Being Tested
 - `standby_for_continuity`: Standby for Continuity
 - `lent_out`: Lent Out
 - `in_production`: In Production
 - `undergoing_maintenance`: Undergoing Maintenance
 - `broken_down`: Broken Down
 - `being_repaired`: Being Repaired
 - `archived`: Archived
 - `to_be_removed`: To Be Removed
 - `lost_or_stolen`: Lost or Stolen
 - `removed`: Removed

supplier
: *Optional* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is used to select the supplier from which the configuration item (CI) has been obtained. When creating a new CI and a value is not specified for this field, it is set to the supplier of the CI’s product.

support\_team
: *Optional* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Support team field is used to select the [Team](../teams.html) responsible for supporting the configuration item and maintaining its information in the configuration management database (CMDB). When creating a new CI and a value is not specified for this field, it is set to the support team of the CI’s product. Optional when status of CI equals “Removed”, required otherwise.

systemID
: *Optional* **[string](../general/data_types.html) (max 255)**

temporary\_license
: *Optional* **[boolean](../general/data_types.html)** — The Temporary license box is checked for license certificates that are not valid indefinitely.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the configuration item. If the configuration item has no updates it contains the `created_at` value.

warranty\_expiry\_date
: *Optional* **[date](../general/data_types.html)** — The Warranty expiry date field is used to specify the date through which the warranty coverage for the configuration item is valid. The warranty expires at the end of this day.

workflow\_template
: *Optional* **[reference](../general/data_types.html#references) to [Workflow Template](../workflow_templates.html)** — The workflow template that is used to periodically maintain the configuration item.

workflow\_manager
: *Optional* **[reference](../general/data_types.html#references) to [Person](../people.html)** — The person who will be responsible for coordinating the workflows that will be generated automatically in accordance with the recurrence schedule.
