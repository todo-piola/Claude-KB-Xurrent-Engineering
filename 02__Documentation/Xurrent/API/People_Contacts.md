# People - Contacts API

**Tip**: If you are looking for information on how to integrate Active Directory or another LDAP system with Xurrent, please refer to the [Directory Services](../../import/directory_services/index.html) page of the [Import API](../../import.html).

- [List all contacts of a person](../contacts.html#list-all-contacts-of-a-person)
- [Get a single contact of a person](../contacts.html#get-a-single-contact-of-a-person)
- [Add a contact to a person](../contacts.html#add-a-contact-to-a-person)
- [Update a contact of a person](../contacts.html#update-a-contact-of-a-person)
- [Remove a contact from a person](../contacts.html#remove-a-contact-from-a-person)
- [Remove all contacts from a person](../contacts.html#remove-all-contacts-from-a-person)
- [Fields](../contacts.html#fields)

## List all contacts of a person

List all [contacts](../../contacts/index.html) of a person with a specific ID:

```
GET /people/:id/contacts
```

### Response

```
status: 200 OK
```

```
[{"label":"mobile","id":1720,"telephone":"+1 03 413 7223"},{"label":"personal","id":1826,"website":"www.my-stie.com"}]
```

The response contains [these fields](../../contacts/index.html#collection-fields) by default.

## Get a single contact of a person

```
GET /people/:id/contacts/:id
```

### Response

```
status: 200 OK
```

```
{"label":"mobile","id":1720,"telephone":"+1 03 413 7223","integration":true}
```

The response contains [these fields](../contacts.html#fields).

## Add a contact to a person

Add a contact to a person with a specific ID.

```
POST /people/:id/contacts
```

When creating a new contact for a person [these fields](../contacts.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"label":"work","...":"..."}
```

The response contains [all fields](../contacts.html#fields) of the created contact and is similar to the response in [Get a single contact of a person](../contacts.html#get-a-single-contact-of-a-person)

## Update a contact of a person

Update a contact with a specific ID of a person with a specific ID.

```
PATCH /people/:id/contacts/:contact_id
```

When updating an existing contact for a person [these fields](../contacts.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"label":"work","...":"..."}
```

The response contains [all fields](../contacts.html#fields) of the created contact and is similar to the response in [Get a single contact of a person](../contacts.html#get-a-single-contact-of-a-person)

## Remove a contact from a person

Remove a contact with a specific ID link from a person with a specific ID.

```
DELETE /people/:id/contacts/:contact_id
```

### Response

```
status: 204 No Content
```

## Remove all contacts from a person

Remove all contacts from a person with a specific ID.

```
DELETE /people/:id/contacts/
```

### Response

```
status: 204 No Content
```

## Fields

email
: *Optional* **[string](../../general/data_types.html) (max 255)** — The Email field is used to enter the person’s work or personal email address.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the contact.

integration
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — The Integration field is a hidden checkbox that can be set to `true` using this API or the Import functionality. When checked, the contact is displayed as read-only in the user interface to prevent users from updating it.

label
: *Required* **[enum](../../general/enumerations/index.html)** — The Label of the contact details. Valid values are:

 - `chat_skype`: only for `chat`
 - `chat_slack`: only for `chat`
 - `chat_teams`: only for `chat`
 - `chat_workchat`: only for `chat`
 - `fax`: only for `telephone`
 - `home`: only for `telephone`
 - `mobile`: only for `telephone`
 - `personal`: only for `email` and `website`
 - `work`: only for `telephone`, `email` and `website`

telephone
: *Optional* **[string](../../general/data_types.html) (max 255)** — The Telephone field is used to enter the person’s work, mobile, home, or fax number.

chat
: *Optional* **[string](../../general/data_types.html) (max 255)** — The Chat field is used to enter the link that can be used to start a direct chat with the person. A separate link can be entered for each chat application that the person uses.

website
: *Optional* **[string](../../general/data_types.html) (max 255)** — The Website field is used to enter the person’s work or personal website URL.

verified
: *Readonly* **[boolean](../../general/data_types.html)** — Indicates whether the email address has been verified.
