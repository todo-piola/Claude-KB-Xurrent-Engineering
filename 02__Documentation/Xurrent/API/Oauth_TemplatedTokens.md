# Templated Tokens

Templated tokens let third-party integrations provide users with a URL that opens the
Personal Access Token or OAuth Application creation form with pre-filled values. This
simplifies onboarding for integrations that need specific API permissions — users only
need to click a link and confirm.

## URL Format

Templated token URLs use the standard Xurrent UI base URL
(*https://<account>.<region>.<domain>*) with the following paths:

**Personal Access Tokens:**

`/personal_access_tokens/new?name=<name>&scopes=<scopes>`

**OAuth Applications:**

`/oauth_applications/new?name=<name>&scopes=<scopes>&grant_type=<grant_type>`

### Parameters

name
: *Required* **[string](../../general/data_types.html)** - Name of the token or
 application (max 128 characters, URL-encoded).

scopes
: *Required* **[string](../../general/data_types.html)** - Comma-separated list of
 scopes in `model:action` format. See [Scope Format](index.html#scope-format) below.

grant\_type
: *OAuth apps only* **[string](../../general/data_types.html)** - Must be
 `client_credentials`, `authorization_code`, or `token_exchange`.

## Scope Format

Scopes follow the `model:action` pattern. Actions can be specified in several ways:

- **Full action names** — `request:Read`, `ci:Create`
- **CRUD shorthand** — `R` = Read, `C` = Create, `U` = Update, `D` = Delete (e.g. `request:RU` for Read and Update)
- **Wildcard** — `request:*` for all available actions on a model

Multiple scopes are separated by commas: `request:RU,problem:RU`

## Examples

### Personal Access Token

#### Read service instances (CRUD shorthand)

- Demo: *https://wdc.xurrent-demo.com/personal\_access\_tokens/new?name=Service+Monitor&scopes=service-instance:R*
- QA: *https://wdc.xurrent.qa/personal\_access\_tokens/new?name=Service+Monitor&scopes=service-instance:R*
- Production (global): *https://wdc.xurrent.com/personal\_access\_tokens/new?name=Service+Monitor&scopes=service-instance:R*
- Production (US): *https://wdc.us.xurrent.com/personal\_access\_tokens/new?name=Service+Monitor&scopes=service-instance:R*

#### Full access to request templates (wildcard)

- Demo: *https://wdc.xurrent-demo.com/personal\_access\_tokens/new?name=Template+Manager&scopes=request-template:\**

#### Multiple scopes (read/update requests + read/update problems)

- Production (global): *https://wdc.xurrent.com/personal\_access\_tokens/new?name=Issue+Tracker&scopes=request:RU,problem:RU*

### OAuth Application

#### Client credentials grant

- Production (UK): *https://globalnet.uk.xurrent.com/oauth\_applications/new?name=Sync+Tool&grant\_type=client\_credentials&scopes=request:R,problem:RU*

#### Authorization code grant

- Production (global): *https://wdc.xurrent.com/oauth\_applications/new?name=Web+App&grant\_type=authorization\_code&scopes=request:R*
