# Holidays API

- [List holidays](../holidays.html#list-holidays)
- [Get a single holiday](../holidays.html#get-a-single-holiday)
- [Create a holiday](../holidays.html#create-a-holiday)
- [Update a holiday](../holidays.html#update-a-holiday)
- [Fields](../holidays.html#fields)

## List holidays

List all holidays for an account:

```
GET /holidays
```

### Response

```
status: 200 OK
```

```
[{"picture_uri":null,"name":"2016 Company BBQ","created_at":"2016-03-14T03:09:42-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:42-06:00","end_at":"2016-06-18T00:00:00","start_at":"2016-06-17T16:00:00","id":4,"source":null},{"picture_uri":null,"name":"Christmas 2010","created_at":"2016-03-14T03:09:42-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:42-06:00","end_at":"2010-12-26T00:00:00","start_at":"2010-12-25T00:00:00","id":2,"source":null},"..."]
```

The response contains [these fields](../holidays.html#collection-fields) by default. [Filtering](../holidays.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of holidays.

### Collection Fields

By default the following [fields](../holidays.html#fields) will appear in collections of holidays:

`id` `source` `sourceID` `name` `picture_uri` `start_at` `end_at` `created_at` `updated_at`

Obtain a different set of [fields](../holidays.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../holidays.html#fields):

`id` `sourceID` `name` `start_at` `end_at` `created_at` `updated_at`

The filters on `sourceID`, and `name` are not case sensitive.

### Sorting

By default a collection of holidays is sorted **ascending** by `name`.

The following [fields](../holidays.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single holiday

```
GET /holidays/:id
```

### Response

```
status: 200 OK
```

```
{"picture_uri":null,"name":"2016 Company BBQ","created_at":"2016-03-14T03:09:42-06:00","sourceID":null,"updated_at":"2016-03-14T03:09:42-06:00","end_at":"2016-06-18T00:00:00","start_at":"2016-06-17T16:00:00","id":4,"source":null}
```

The response contains [these fields](../holidays.html#fields).

## Create a holiday

```
POST /holidays
```

When creating a new holiday [these fields](../holidays.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](../holidays.html#fields) of the created holiday and is similar to the response in [Get a single holiday](../holidays.html#get-a-single-holiday)

## Update a holiday

```
PATCH /holidays/:id
```

When updating a holiday [these fields](../holidays.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](../holidays.html#fields) of the updated holiday and is similar to the response in [Get a single holiday](../holidays.html#get-a-single-holiday)

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the holiday was created.

end\_at
: *Required* **[datetime](../general/data_types.html)**

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the holiday.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the holiday.

picture\_uri
: *Optional* **[string](../general/data_types.html)** — The hyperlink to the image file for the holiday. When setting this value a [data URL](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data) can be used to supply the image directly, removing the need for a separate upload.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

start\_at
: *Required* **[datetime](../general/data_types.html)**

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the holiday. If the holiday has no updates it contains the `created_at` value.
