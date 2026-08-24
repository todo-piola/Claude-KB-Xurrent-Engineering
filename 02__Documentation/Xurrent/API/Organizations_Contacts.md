# Organizations - Contacts API

- [List all contacts of an organization](index.html#list-all-contacts-of-an-organization)
- [Get a single contact of an organization](index.html#get-a-single-contact-of-an-organization)
- [Add a contact to an organization](index.html#add-a-contact-to-an-organization)
- [Update a contact of an organization](index.html#update-a-contact-of-an-organization)
- [Remove a contact from an organization](index.html#remove-a-contact-from-an-organization)
- [Remove all contacts from an organization](index.html#remove-all-contacts-from-an-organization)
- [Fields](index.html#fields)

## List all contacts of an organization

List all [contacts](../../contacts/index.html) of the organization with a specific ID:

```
GET /organizations/:id/contacts
```

### Response

```
status: 200 OK
```

```
[{"label":"general","id":68,"telephone":"+1 (203) 413 4880"},{"label":"service_desk","id":67,"telephone":"+1 (800) 4-BEST-IT or +1 (800) 423 7848"},{"label":"fax","id":70,"telephone":"+1 (203) 413 4881"},{"label":"general","id":65,"email":"info@best-it.com"},{"label":"service_desk","id":69,"email":"helpdesk@best-it.com"},{"label":"general","id":66,"website":"www.best-it.com"},{"label":"service_desk","id":71,"website":"www.support.best-it.com"}]
```

The response contains [these fields](../../contacts/index.html#collection-fields) by default.

## Get a single contact of an organization

```
GET /organizations/:id/contacts/:contact_id
```

### Response

```
status: 200 OK
```

```
{"id":68,"label":"general","telephone":"+1 (203) 413 4880","integration":true}
```

The response contains [these fields](index.html#fields).

## Add a contact to an organization

Add a contact to an organization with a specific ID.

```
POST /organizations/:id/contacts
```

When creating a new contact for an organization [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"label":"general","...":"..."}
```

The response contains [all fields](index.html#fields) of the created contact and is similar to the response in [Get a single contact of an organization](index.html#get-a-single-contact-of-an-organization)

## Update a contact of an organization

Update a contact with a specific ID of an organization with a specific ID.

```
PATCH /organizations/:id/contacts/:contact_id
```

When updating an existing contact for an organization [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"label":"general","...":"..."}
```

The response contains [all fields](index.html#fields) of the created contact and is similar to the response in [Get a single contact of an organization](index.html#get-a-single-contact-of-an-organization)

## Remove a contact from an organization

Remove a contact with a specific ID from an organization with a specific ID.

```
DELETE /organizations/:id/contacts/:contact_id
```

### Response

```
status: 204 No Content
```

## Remove all contacts from an organization

Remove all contacts from an organization with a specific ID.

```
DELETE /organizations/:id/contacts/
```

### Response

```
status: 204 No Content
```

## Fields

email
: *Optional* **[string](../../general/data_types.html) (max 255)** — The Email field is used to enter the organization’s general or service desk email address.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the contact.

integration
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — The Integration field is a hidden checkbox that can be set to `true` using this API or the Import functionality. When checked, the contact is displayed as read-only in the user interface to prevent users from updating it.

label
: *Required* **[enum](../../general/enumerations/index.html)** — The Label of the contact details. Valid values are:
: - `general`
 - `service_desk`
 - `fax`: only for `telephone`
 - `service_desk_fax`: only for `telephone`

telephone
: *Optional* **[string](../../general/data_types.html) (max 255)** — The Telephone field is used to enter the organization’s general, fax, service desk, or service desk fax number.

website
: *Optional* **[string](../../general/data_types.html) (max 255)** — The Website field is used to enter the organization’s general or service desk website URL.
