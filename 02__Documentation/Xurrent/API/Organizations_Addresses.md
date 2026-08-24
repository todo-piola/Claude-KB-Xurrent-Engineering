# Organizations - Addresses API

- [List all addresses of an organization](index.html#list-all-addresses-of-an-organization)
- [Get a single address of an organization](index.html#get-a-single-address-of-an-organization)
- [Add an address to an organization](index.html#add-an-address-to-an-organization)
- [Update an address of an organization](index.html#update-an-address-of-an-organization)
- [Remove an address from an organization](index.html#remove-an-address-from-an-organization)
- [Remove all addresses from an organization](index.html#remove-all-addresses-from-an-organization)
- [Fields](index.html#fields)

## List all addresses of an organization

List all [addresses](../../addresses/index.html) of the organization with a specific ID:

```
GET /organizations/:id/addresses
```

### Response

```
status: 200 OK
```

```
[{"address":"18 Kings Highway North","city":"Westport","label":"street","zip":"6880","country":"US","id":34,"state":"CT"},{"address":"P.O. Box 15120","city":"Albany","label":"mailing","zip":"12212-5120","country":"US","id":164,"state":"NY"}]
```

The response contains [these fields](../../addresses/index.html#collection-fields) by default.

## Get a single address of an organization

```
GET /organizations/:id/addresses/:id
```

### Response

```
status: 200 OK
```

```
{"id":34,"label":"street","address":"18 Kings Highway North","city":"Westport","state":"CT","zip":"6880","country":"US","integration":true}
```

The response contains [these fields](index.html#fields).

## Add an address to an organization

Add an address to an organization with a specific ID.

```
POST /organizations/:id/addresses
```

When creating a new address for an organization [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"label":"street","...":"..."}
```

The response contains [all fields](index.html#fields) of the created address and is similar to the response in [Get a single address of an organization](index.html#get-a-single-address-of-an-organization)

## Update an address of an organization

Update an address with a specific ID of an organization with a specific ID.

```
PATCH /organizations/:id/addresses/:address_id
```

When updating an existing address for an organization [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"label":"street","...":"..."}
```

The response contains [all fields](index.html#fields) of the created address and is similar to the response in [Get a single address of an organization](index.html#get-a-single-address-of-an-organization)

## Remove an address from an organization

Remove an address with a specific ID from an organization with a specific ID.

```
DELETE /organizations/:id/addresses/:address_id
```

### Response

```
status: 204 No Content
```

## Remove all addresses from an organization

Remove all addresses from an organization with a specific ID.

```
DELETE /organizations/:id/addresses/
```

### Response

```
status: 204 No Content
```

## Fields

address
: *Optional* **[string](../../general/data_types.html) (max 1024)** — The address lines.

city
: *Optional* **[string](../../general/data_types.html) (max 128)** — The city name.

country
: *Optional* **[string](../../general/data_types.html) (max 128)** — The 2-letter country code.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the address.

integration
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — The Integration field is a hidden checkbox that can be set to `true` using this API or the Import functionality. When checked, the address is displayed as read-only in the user interface to prevent users from updating it.

label
: *Required* **[enum](../../general/enumerations/index.html)** — The Label of the address details. Valid values are:
: - `street`
 - `mailing`
 - `billing`

state
: *Optional* **[string](../../general/data_types.html) (max 30)** — The state name.

zip
: *Optional* **[string](../../general/data_types.html) (max 20)** — The zip code.
