# People - Addresses API

**Tip**: If you are looking for information on how to integrate Active Directory or another LDAP system with Xurrent, please refer to the [Directory Services](../../import/directory_services/index.html) page of the [Import API](../../import.html).

- [List all addresses of a person](../addresses.html#list-all-addresses-of-a-person)
- [Get a single address of a person](../addresses.html#get-a-single-address-of-a-person)
- [Add an address to a person](../addresses.html#add-an-address-to-a-person)
- [Update an address of a person](../addresses.html#update-an-address-of-a-person)
- [Remove an address from a person](../addresses.html#remove-an-address-from-a-person)
- [Remove all addresses from a person](../addresses.html#remove-all-addresses-from-a-person)
- [Fields](../addresses.html#fields)

## List all addresses of a person

List all [addresses](../../addresses/index.html) of a person with a specific ID:

```
GET /people/:id/addresses
```

### Response

```
status: 200 OK
```

```
[{"address":"18 Kings Highway North","city":"Westport","label":"home","zip":"6880","country":"US","id":34,"state":"CT"},{"address":"P.O. Box 15120","city":"Albany","label":"mailing","zip":"12212-5120","country":"US","id":164,"state":"NY"}]
```

The response contains [these fields](../../addresses/index.html#collection-fields) by default.

## Get a single address of a person

```
GET /people/:id/addresses/:id
```

### Response

```
status: 200 OK
```

```
{"address":"18 Kings Highway North","city":"Westport","label":"home","zip":"6880","country":"US","id":34,"state":"CT","integration":false}
```

The response contains [these fields](../addresses.html#fields).

## Add an address to a person

Add an address to a person with a specific ID.

```
POST /people/:id/addresses
```

When creating a new address for a person [these fields](../addresses.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"label":"home","...":"..."}
```

The response contains [all fields](../addresses.html#fields) of the created address and is similar to the response in [Get a single address of a person](../addresses.html#get-a-single-address-of-a-person)

## Update an address of a person

Update an address of a person with a specific ID.

```
PATCH /people/:id/addresses/:address_id
```

When updating an existing address for a person [these fields](../addresses.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"label":"home","...":"..."}
```

The response contains [all fields](../addresses.html#fields) of the created address and is similar to the response in [Get a single address of a person](../addresses.html#get-a-single-address-of-a-person)

## Remove an address from a person

Remove an address with a specific ID from a person with a specific ID.

```
DELETE /people/:id/addresses/:address_id
```

### Response

```
status: 204 No Content
```

## Remove all addresses from a person

Remove all addresses from a person with a specific ID.

```
DELETE /people/:id/addresses/
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
: - `home`
 - `mailing`

state
: *Optional* **[string](../../general/data_types.html) (max 30)** — The state name.

zip
: *Optional* **[string](../../general/data_types.html) (max 20)** — The zip code.
