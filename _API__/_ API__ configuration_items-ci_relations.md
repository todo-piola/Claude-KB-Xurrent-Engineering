# Configuration Items - CI Relations API

**Tip**: If you are looking for information on how to integrate a discovery tool with Xurrent, please refer to the [Discovery Tools](../../import/discovery_tools/index.html) page of the [Import API](../../import.html).

- [List all CI relations of a configuration item](index.html#list-all-ci-relations-of-a-configuration-item)
- [Add a CI relation to a configuration item](index.html#add-a-ci-relation-to-a-configuration-item)
- [Update a CI relation of a configuration item](index.html#update-a-ci-relation-of-a-configuration-item)
- [Remove a CI relation from a configuration item](index.html#remove-a-ci-relation-from-a-configuration-item)
- [Remove all CI relations from a configuration item](index.html#remove-all-ci-relations-from-a-configuration-item)
- [Fields](index.html#fields)

## List all CI relations of a configuration item

List all [CI relations](../../ci_relations/index.html) of the configuration item with a specific ID:

```
GET /cis/:id/ci_relations
```

### Response

```
status: 200 OK
```

```
[{"id":"4558","ci":{"name":"HP Compaq dc7900 Minitower PC","label":"CMP00021","id":339},"relation_type":"parent"},{"id":324,"ci":{"name":"HP Compaq dc7900 Minitower PC","label":"CMP00022","id":340},"relation_type":"parent"}]
```

The response contains [these fields](../../ci_relations/index.html#collection-fields) by default.

## Add a CI relation to a configuration item

Add a CI relation to a configuration item with a specific ID.

```
POST /cis/:id/ci_relations
```

When creating a new CI relation for a configuration item [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":4558,"ci":{"id":1776,"label":"CMP00014","name":"HP 9000 rp4410 SAP North America Production Server"},"relation_type":"parent"}
```

## Update a CI relation of a configuration item

Update a CI relation with a specific ID of a configuration item with a specific ID.

```
PATCH /cis/:id/ci_relations/:ci_relation_id
```

When updating an existing CI relation for a configuration item [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"relation_type":"parent","...":"..."}
```

## Remove a CI relation from a configuration item

Remove a CI relation with a specific ID link from a configuration item with a specific ID.

```
DELETE /cis/:id/ci_relations/:ci_relation_id
```

### Response

```
status: 204 No Content
```

## Remove all CI relations from a configuration item

Remove all CI relations from a configuration item with a specific ID.

```
DELETE /cis/:id/ci_relations/
```

### Response

```
status: 204 No Content
```

## Fields

related\_ci\_id
: *Required* **[reference](../../general/data_types.html#references) to [configuration item](../index.html)** — The ID of the related configuration item.

relation\_type
: *Required* **[enum](../../general/enumerations/index.html)** — The type of the relation. Valid values are:
: - `parent`: Use this relation type to link a software CI to the software suite or software distribution package that it is a module or application of. Also use this relation type to link a virtual machine, software distribution package or software CI to the physical computers on which it has been installed. This relation type is also used to link a hardware CI to the hardware CI that it is a component of, installed in, or directly connected to (not using the network). In case of an address CI, this relation type is used to create a link with the CI to which the address has been assigned.
 - `child`: Use this relation type to link a software suite or software distribution package to the software modules or applications that it is made up of. Also use this relation type to link a physical computer to the virtual machines, software distribution packages or software CIs that have been installed on it. This relation type is also used to link a hardware CI to its hardware components, CIs that have been installed in it, and CIs that are directly connected to it (not using the network). It is also used to link the addresses that have been assigned to it.
 - `network_connection`: Use this relation type to link a hardware CI to all other hardware CIs that have a direct network connection with this CI (e.g. a router to a switch).
 - `redundancy`: Use this relation type to link a hardware CI to all other hardware CIs that provide it redundancy. For example, a server that forms a cluster with another server.
 - `continuity`: Use this relation type to link a hardware CI to another hardware CI that is located at another site and which is to be used as replacement in case the service instance that the first hardware CI supports needs to be recovered at its continuity site.
 - `software_dependency`: Use this relation type to link a software CI to all other software CIs, software/interface configurations and databases that depend on this software CI, or which the software CI depends on.
