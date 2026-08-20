# Sites API

- [List sites](../sites.html#list-sites)
- [Get a single site](../sites.html#get-a-single-site)
- [Create a site](../sites.html#create-a-site)
- [Update a site](../sites.html#update-a-site)
- [Fields](../sites.html#fields)

## List sites

List all sites for an account:

```
GET /sites
```

### Response

```
status: 200 OK
```

```
[{"name":"Widget Data Center","created_at":"2016-03-14T03:09:52-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:52-06:00","id":13},{"name":"IT Training Facility","created_at":"2016-03-14T09:10:17-06:00","sourceID":null,"updated_at":"2014-01-18T11:29:02-06:00","id":29,"disabled":true},"..."]
```

The response contains [these fields](../sites.html#collection-fields) by default. [Filtering](../sites.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of sites.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/sites/disabled`: List all disabled sites
- `/sites/enabled`: List all enabled sites
- `/sites/directory`: List all sites registered in the directory account of the support domain account from which the data is requested
- `/sites/support_domain`: List all sites registered in the account from which the data is requested

### Collection Fields

By default the following [fields](../sites.html#fields) will appear in collections of sites:

`id` `sourceID` `name` `created_at` `updated_at`

Obtain a different set of [fields](../sites.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../sites.html#fields):

`id` `source` `sourceID` `name` `disabled` `created_at` `updated_at`

### Sorting

By default a collection of sites is sorted **ascending** by `name`.

The following [fields](../sites.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single site

```
GET /sites/:id
```

### Response

```
status: 200 OK
```

```
{"picture_uri":null,"name":"Widget Data Center","city":"Houston","address":"1919 Briar Oaks Lane","zip":"77027","remarks":null,"created_at":"2016-03-14T03:09:52-06:00","sourceID":null,"country":"US","updated_at":"2016-03-14T03:09:52-06:00","id":13,"time_zone":"Central Time (US & Canada)","source":null,"disabled":false,"state":"TX","custom_fields":null,"ui_extension":null}
```

The response contains [these fields](../sites.html#fields).

## Create a site

```
POST /sites
```

When creating a new site [these fields](../sites.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"address":"...","...":"..."}
```

The response contains [all fields](../sites.html#fields) of the created site and is similar to the response in [Get a single site](../sites.html#get-a-single-site)

## Update a site

```
PATCH /sites/:id
```

When updating an existing site [these fields](../sites.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"address":"...","...":"..."}
```

The response contains [all fields](../sites.html#fields) of the updated site and is similar to the response in [Get a single site](../sites.html#get-a-single-site)

## Fields

address
: *Optional* **[string](../general/data_types.html) (max 1024)** — The address lines of the street address.

attachments
: *Readonly* **aggregated Attachments**

city
: *Optional* **[string](../general/data_types.html) (max 80)** — The city name of the street address.

country
: *Optional* **[string](../general/data_types.html) (max 128)** — The 2-letter country code of the street address.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the site was created.

custom\_fields
: *Optional* **[custom fields](../general/data_types.html)** — Custom fields provided in JSON format by the [UI Extension](../ui_extensions.html) that is linked to the site.

custom\_fields\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in Custom fields.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the site may no longer be related to other records.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the site.

integration
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Integration field is a hidden checkbox that can be set to `true` using this API or the Import functionality. When checked, the address fields of the site are displayed as read-only in the user interface to prevent users from updating them.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the site or facility.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the site. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

remarks
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Remarks field is used to add any additional information about the site that might prove useful.

remarks\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Remarks field.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

state
: *Optional* **[string](../general/data_types.html) (max 30)** — The state name of the street address.

time\_zone
: *Optional* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone in which the site is located.

ui\_extension
: *Readonly* **[reference](../general/data_types.html#references) to [UI Extension](../ui_extensions.html)** — The UI extension field indicates the UI extension that is applied to the site.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the site. If the site has no updates it contains the `created_at` value.

zip
: *Optional* **[string](../general/data_types.html) (max 20)** — The zip code of the street address.
