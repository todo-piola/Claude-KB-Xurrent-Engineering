# Addresses API

Addresses are aggregated within [people](../people.html), [organizations](../organizations.html) and [sites](../sites.html).

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of contacts:

`label` `uri`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Sorting

Collections of contacts are sorted **ascending** by `label`.

## Fields

address
: *Optional* **[string](../general/data_types.html) (max 1024)** — The address lines.

addressable
: *Required* **[reference](../general/data_types.html#references) to [Person](../people.html), [Organization](../organizations.html) or [Site](../sites.html)** — The entity to address.

city
: *Optional* **[string](../general/data_types.html) (max 128)** — The city name.

country
: *Optional* **[string](../general/data_types.html) (max 128)** — The country name.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the address.

integration
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Integration field is a hidden checkbox that can be set to `true` using this API or the Import functionality. When checked, the address is displayed as read-only in the user interface to prevent users from updating it.

label
: *Required* **[enum](../general/enumerations/index.html)** — The Label of the address details. Valid values are:
: - `home`: only for people
 - `street`: only for organizations and sites
 - `mailing`: only for organizations and people
 - `billing`: only for organizations

state
: *Optional* **[string](../general/data_types.html) (max 30)** — The state name.

zip
: *Optional* **[string](../general/data_types.html) (max 20)** — The zip code.
