# Configuration Item Relations API

Configuration item relations belong to a [configuration items](../configuration_items/index.html).

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of configuration items:

`id` `ci` `relation_type`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Sorting

Collections of Contacts are sorted **ascending** by `relation_type`.

### Restrictions

CIs with the category `Software License Certificate` cannot be related to other CIs.

## Fields

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the CI relation.

ci
: *Required* **[reference](../general/data_types.html#references) to [configuration item](../configuration_items/index.html)** — The related configuration item.

relation\_type
: *Required* **[enum](../general/enumerations/index.html)** — The type of the relation. Valid values are:
: - `parent`: Use this relation type to link a software CI to the software suite or software distribution package that it is a module or application of. Also use this relation type to link a virtual machine, software distribution package or software CI to the physical computers on which it has been installed. This relation type is also used to link a hardware CI to the hardware CI that it is a component of, installed in, or directly connected to (not using the network). In case of an address CI, this relation type is used to create a link with the CI to which the address has been assigned.
 - `child`: Use this relation type to link a software suite or software distribution package to the software modules or applications that it is made up of. Also use this relation type to link a physical computer to the virtual machines, software distribution packages or software CIs that have been installed on it. This relation type is also used to link a hardware CI to its hardware components, CIs that have been installed in it, and CIs that are directly connected to it (not using the network). It is also used to link the addresses that have been assigned to it.
 - `network_connection`: Use this relation type to link a hardware CI to all other hardware CIs that have a direct network connection with this CI (e.g. a router to a switch).
 - `redundancy`: Use this relation type to link a hardware CI to all other hardware CIs that provide it redundancy. For example, a server that forms a cluster with another server.
 - `continuity`: Use this relation type to link a hardware CI to another hardware CI that is located at another site and which is to be used as replacement in case the service instance that the first hardware CI supports needs to be recovered at its continuity site.
 - `software_dependency`: Use this relation type to link a software CI to all other software CIs, software/interface configurations and databases that depend on this software CI, or which the software CI depends on.
