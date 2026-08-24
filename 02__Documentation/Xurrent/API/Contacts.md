# Contacts API

Contacts are aggregated within [people](../people.html) and [organizations](../organizations.html).

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of contacts:

`protocol` `label` `uri`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Sorting

Collections of contacts are sorted **ascending** by `protocol` then **ascending** by `label`.

## Fields

contactable
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html) or [Organization](../organizations.html)** — The entity to contact.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the contact.

integration
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Integration field is a hidden checkbox that can be set to `true` using this API or the Import functionality. When checked, the contact is displayed as read-only in the user interface to prevent users from updating it.

protocol
: *Required* **[enum](../general/enumerations/index.html)** — The protocol of the contact details. Valid values are:
: - `telephone`: Telephone
 - `email`: Email
 - `website`: Website

label
: *Required* **[enum](../general/enumerations/index.html)** — The Label of the contact details. Valid values are:
: - `fax`: only for `telephone`
 - `general`: only for organization `telephone`, `email` and `website`
 - `home`: only for person `telephone`
 - `mobile`: only for person `telephone`
 - `personal`: only for person `email` and `website`
 - `service_desk`: only for organization `telephone`, `email` and `website`
 - `service_desk_fax`: only for organization `telephone`
 - `work`: only for organization `telephone`, and for person `telephone`, `email` and `website`

uri
: *Required* **[string](../general/data_types.html) (max 255)** — The telephone number, email address, etc.

verified
: *Readonly* **[boolean](../general/data_types.html)** — Indicates whether the email address has been verified. Only applicable to `email` contact details of [people](../people.html).
