# Source and Source ID

The `source` and `sourceID` fields keep track of where resources originate from.
The `source` field is used to specify the name of the external system from which
the data of a Xurrent record was obtained. The `sourceID` field is used to specify
the unique identifier or number that can be used to find the record in the
source system. When the data that is stored in Xurrent originates from multiple
external systems, the combination of these two fields is used to uniquely
identify records in the correct source system.

When building an integration with Xurrent its is recommended to fill out both these
fields while importing resources from an external system into Xurrent.

An update of the `source` and `sourceID` field values of a record can only be
performed by an API user who has the [Account Administrator
role](../../index.html#authentication) of the account to which the
record belongs. If the Account Administrator role does not provide write access
to the type of record that needs to be updated, then the API user will also need
another role that does give write access to this record type. For example, if an
API user needs to be able to update the `source` and `sourceID` field values of
requests, then this API user will need to have the Specialist role, as well as
the Account Administrator role, of the account to which the requests belong.

source
: an identifier for the client application submitting the resource or the name of an external system (limited to 30 characters)

sourceID
: the unique identifier of the resource in an external system (limited to 128 characters)

## Source

The `source` field is filled on creation of a resource with the first non-empty value from:

- The `source` field as a normal parameter
- HTTP header `X-Xurrent-Source`
- HTTP header `User-Agent`

If all are empty it defaults to the value `"Xurrent API"`.

## Source ID

The `sourceID` field should be passed as a normal parameter.

When references to resources with a Source ID are retrieved from the API, the `sourceID`
field will always be provided, see [references](../data_types.html#source-id).

## Example

```
 $ curl -X POST -H 'X-Xurrent-Source: SomeSD' \
 -d '{"name":"OurServiceDesk", "sourceID":"N1C3AP1"}' \
 https://api.xurrent.com/v1/teams
```

```
status: 201 Created
```

```
{"id":23,"name":"OurServiceDesk","source":"SomeSD","sourceID":"N1C3AP1"}
```

*Not all request fields are shown above to keep the example simple.*
