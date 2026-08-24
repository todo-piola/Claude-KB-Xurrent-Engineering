# Parent Service Instances API

Parent Service Instances belong to a [Service Level Agreement](../service_level_agreements.html).

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of parent service instances:

`id` `service_instance` `impact_relation`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Sorting

Collections of service instances are sorted **ascending** by `service_instance.name`.

## Fields

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the Parent Service Instance relation.

service\_instance
: *Required* **[reference](../general/data_types.html#references) to [service\_instance](../service_instances/index.html)** — The linked service instance.
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

impact\_relation
: *Required* **[enum](../general/enumerations/index.html)** — The type of the relation. Valid values are:

 - `degraded`: Degraded if Service Instance of SLA is Down or Degraded
 - `down`: Down if Service Instance of SLA is Down
: This field cannot be specified in the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).
