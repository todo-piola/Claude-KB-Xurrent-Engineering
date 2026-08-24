# People - Permissions API

- [List permissions of a person](../permissions.html#list-permissions-of-a-person)
- [List permissions of a person for a specific account](../permissions.html#list-permissions-of-a-person-for-a-specific-account)
- [List people of account with specific roles](../permissions.html#list-people-of-account-with-specific-roles)
- [List people with specific roles of account](../permissions.html#list-people-with-specific-roles-of-account)
- [Add roles to a person](../permissions.html#add-roles-to-a-person)
- [Overwrite the roles of a person](../permissions.html#overwrite-the-roles-of-a-person)
- [Revoke roles from a person](../permissions.html#revoke-roles-from-a-person)
- [Revoke all roles of an account from a person](../permissions.html#revoke-all-roles-of-an-account-from-a-person)
- [Revoke all roles from a person](../permissions.html#revoke-all-roles-from-a-person)
- [Fields](../permissions.html#fields)

## List permissions of a person

List all permissions of a [person](../../people.html) with the given *:id*.

```
GET /people/:id/permissions
```

### Response

```
status: 200 OK
```

```
[{"account":{"id":"widget","name":"Widget International"},"roles":["directory_administrator"]},{"account":{"name":"Widget Data Center","id":"wdc"},"roles":["specialist","service_desk_analyst","service_desk_manager","knowledge_manager","problem_manager","workflow_manager","release_manager","project_manager","service_level_manager","configuration_manager","account_administrator","account_owner"]},{"account":{"name":"Widget North America","id":"wna"},"roles":["account_administrator"]},{"account":{"name":"Widget Europe","id":"weu"},"roles":["account_administrator"]}]
```

The response contains [these fields](../permissions.html#fields) by default.

## List permissions of a person for a specific account

List all permissions of a [person](../../people.html) with the given *:id* for the account with the given *:accountID*.

```
GET /people/:id/permissions/:accountID
```

### Response

```
status: 200 OK
```

```
{"account":{"name":"Widget Data Center","id":"wdc"},"roles":["specialist","service_desk_analyst","service_desk_manager","knowledge_manager","problem_manager","workflow_manager","release_manager","project_manager","service_level_manager","configuration_manager","account_administrator","account_owner"]}
```

The response contains [these fields](../permissions.html#fields) by default.

## List people of account with specific roles

Returns all the person records that are registered in the account and its directory account, provided that these people have at least one of the specified roles.

```
GET /people?roles=role1,role2,...
```

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: widget" \
 -X GET \
 "https://api.xurrent.com/v1/people?roles=directory_administrator,directory_auditor"
```

### Response

The response contains [these fields](../../people.html#collection-fields) by default. [Filtering](../../people.html#filtering) and [pagination](../../general/pagination.html) are available to reduce/limit the collection of people.

## List people with specific roles of account

Returns all the person records that have at least one of the specified roles of the account.

```
GET /people/all_with_roles?roles=role1,role2,...
```

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" \
 -H "X-Xurrent-Account: wdc" \
 -X GET \
 "https://api.xurrent.com/v1/people/all_with_roles?roles=specialist,problem_manager"
```

### Response

The response contains [these fields](../../people.html#collection-fields) by default. [Filtering](../permissions.html#filtering) and [pagination](../../general/pagination.html) are available to reduce/limit the collection of people.

## Add roles to a person

Adds the specified roles of the account to a person.

```
POST /people/:id/permissions/:accountID?roles=role1,role2,...
```

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" -X POST -H "X-Xurrent-Account: widget" "https://api.xurrent.com/v1/people/1234/permissions/wdc?roles=specialist,problem_manager"
```

### Response

The response contains [these fields](../permissions.html#fields) by default.

## Overwrite the roles of a person

Overwrite the roles that a person has of the account with the specified roles of the account.

```
PATCH /people/:id/permissions/:accountID?roles=role1,role2,...
```

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" -X PATCH -H "X-Xurrent-Account: widget" "https://api.xurrent.com/v1/people/1234/permissions/wdc?roles=problem_manager,workflow_manager"
```

### Response

The response contains [these fields](../permissions.html#fields) by default.

## Revoke roles from a person

Remove the specified roles of the account from a person.

```
DELETE /people/:id/permissions/:accountID?roles=role1,role2,...
```

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" -X DELETE -H "X-Xurrent-Account: widget" "https://api.xurrent.com/v1/people/1234/permissions/wdc?roles=problem_manager,workflow_manager"
```

### Response

```
status: 204 No Content
```

## Revoke all roles of an account from a person

Remove all roles of the specified account from a person.

```
DELETE /people/:id/permissions/:accountID
```

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" -X DELETE -H "X-Xurrent-Account: widget" "https://api.xurrent.com/v1/people/1234/permissions/wdc"
```

### Response

```
status: 204 No Content
```

## Revoke all roles from a person

Remove all roles in all accounts from a person.

```
DELETE /people/:id/permissions
```

Example:

```
 $ curl -H "Authorization: Bearer <oauth-token>" -X DELETE -H "X-Xurrent-Account: widget" "https://api.xurrent.com/v1/people/1234/permissions"
```

Note:

- You must be administrator in the account of the specified person.
- It is not allowed to remove your own permissions.

### Response

```
status: 204 No Content
```

## Fields

account
: *Required* **[reference](../../general/data_types.html#references) to [Account](../../general/data_types.html#account)** — The account for which the person has permissions

roles
: *Required* **array of [enum](../../general/enumerations/index.html)** — The roles the person has within the account
: - `key_contact`
 - `auditor`
 - `financial_manager`
 - `directory_auditor` (for directory accounts only)
 - `specialist`
 - `service_desk_analyst`
 - `service_desk_manager`
 - `knowledge_manager`
 - `problem_manager`
 - `workflow_manager`
 - `release_manager`
 - `project_manager`
 - `service_level_manager`
 - `configuration_manager`
 - `account_designer`
 - `account_administrator`
 - `directory_designer` (for directory accounts only)
 - `directory_administrator` (for directory accounts only)
 - `workflow_automator_auditor` (for Xurrent Workflow Automator enabled accounts only)
 - `workflow_automator_specialist` (for Xurrent Workflow Automator enabled accounts only)
 - `account_owner`
