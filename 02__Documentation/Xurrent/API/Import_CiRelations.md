# Configuration Item Relations Import

Configuration Item (CI) records can be related to each other. For each relation a relation type can be specified.

Configuration Item Relations can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Configuration Item Relations import file can be found in [Configuration Item Relations API - Fields](../../ci_relations/index.html#fields).

## CSV Example

```
Source,CI Source,CI Source ID,CI Label,Related CI Source,Related CI Source ID,Related CI Label,Relation Type
MS System Center,,,CMP00021,,,Microsoft Windows 7 Professional SP3,child
MS System Center,MS System Center,65422389,,MS System Center,6503214,,redundancy
```

[download CSV](https://developer.xurrent.com/csv/ci_relations.csv)

The import file below offers an example for relating a server to different CIs using different relation types. This example shows that server CMP00001 forms a server cluster with server CMP00002. This server is located in rack RCK00006, runs HP-UX 11i v3 as its operating system software, and is plugged into router RTR00012. When the data center in which server CMP00001 is located is struck by a disaster, server CMP00072 will be used to replace it (server CMP00072 is located at the recovery site).

```
,,,CMP00001,,,CMP00002,redundancy
,,,CMP00001,,,RCK00006,parent
,,,CMP00001,,,HP-UX 11i v3,child
,,,CMP00001,,,RTR00012,network_connection
,,,CMP00001,,,CMP00072,continuity
```

The following example focuses on establishing relations between software CIs. This example indicates that version 11.1.0.7 of the Oracle database software runs on one or more servers with the HP-UX 11i v3 operating system version. It also indicates that version 6.20.49 of the SAP ERP Central Component software relies on version 11.1.0.7 of the Oracle database software.

```
,,,Oracle 11.1.0.7,,,HP-UX 11i v3,software_dependency
,,,Oracle 11.1.0.7,,,SAP ERP Central Component 6.20.49,software_dependency
```

## Updating Existing Relations

If one or more relations are defined for a Configuration Item in the import file and a `Source` is specified for these relations, then all existing relations of that CI with the same `Source` will be removed during the import.

**Important**: Make sure all relations for a Configuration Item are grouped together in the import file. Otherwise the last relation that is specified for a Configuration Item in the import file will cause the previous relations, which were added during the import for that same Configuration Item, to be removed.

If the [`Source`](../../general/source.html) is not defined for a relation in the import file, then the relation will be added during the import without removing any existing relations.

## Syncing CI Relations in Xurrent to an External System

When one of the relations of a Configuration Item is updated, all relations of that CI will be added to the export.

When the last relation of a Configuration Item is removed, no relations will be present in the Configuration Item Relations export. To keep both systems in sync, the `Has CI Relations` column of the [Configuration Items Export](../cis/index.html) file can be used to detect that situation. When the value is `FALSE` all relations for that particular CI may be removed in the external system.

## Discovery Tool Integrations

Visit the [Discovery Tools](../discovery_tools/index.html) page for more information about how the Import API can be used to import CI relations that have been discovered by system management tools.
