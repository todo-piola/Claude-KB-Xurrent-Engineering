# Webhook Policies API

- [List webhook policies](../webhook_policies.html#list-webhook-policies)
- [Get a webhook policy](../webhook_policies.html#get-a-single-webhook-policy)
- [Create a webhook policy](../webhook_policies.html#create-a-webhook-policy)
- [Update a webhook policy](../webhook_policies.html#update-a-webhook-policy)
- [Delete a webhook policy](../webhook_policies.html#delete-a-webhook-policy)
- [Fields](../webhook_policies.html#fields)

## List webhook policies

List all webhook policies for an account:

```
GET /webhook_policies
```

### Response

```
status: 200 OK
```

```
[{"id":301,"name":"6f3a5394ff9262be392926386113d684915ed1a956910902c29d0baf","created_at":"2015-09-10T12:15:16-05:00","updated_at":"2015-09-14T12:31:27-05:00"},{"id":312,"name":"41c87abb02950b7541ee1d4fcea20cc05cc8a6f361612d7a86cb9577","created_at":"2015-09-10T12:15:16-05:00","updated_at":"2015-09-10T12:15:16-05:00"},"..."]
```

The response contains [these fields](../webhook_policies.html#collection-fields) by default. [Filtering](../webhook_policies.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of webhook policies.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/webhook_policies/disabled`: List all disabled webhook policies
- `/webhook_policies/enabled`: List all enabled webhook policies

### Collection Fields

By default the following [fields](../webhook_policies.html#fields) will appear in collections of webhook policies:

`id` `name` `created_at` `updated_at`

Obtain a different set of [fields](../webhook_policies.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](../webhook_policies.html#fields):

`id` `name` `created_at` `updated_at` `disabled`

The filter on `name` is not case sensitive.

### Sorting

By default a collection of webhook policies is sorted **ascending** by `created_at`.

The following [fields](../webhook_policies.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`created_at` `updated_at`

## Get a single webhook policy

```
GET /webhook_policies/:id
```

### Response

```
status: 200 OK
```

```
{"id":312,"name":"41c87abb02950b7541ee1d4fcea20cc05cc8a6f361612d7a86cb9577","disabled":true,"created_at":"2015-09-10T12:15:16-05:00","updated_at":"2015-09-10T12:15:16-05:00","jwt_alg":"rs256","jwt_audience":"some audience","jwt_claim_expires_in":12}
```

The response contains [these fields](../webhook_policies.html#fields).

## Create a webhook policy

```
POST /webhook_policies
```

When creating a new webhook policy [these fields](../webhook_policies.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../webhook_policies.html#fields) of the created webhook policy and is similar to the response in [Get a single webhook policy](../webhook_policies.html#get-a-single-webhook-policy). This is the only time the `public_key_pem` field will be exposed.

## Update a webhook policy

```
PATCH /webhook_policies/:id
```

When updating a webhook policy [these fields](../webhook_policies.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"name":"...","...":"..."}
```

The response contains [all fields](../webhook_policies.html#fields) of the updated webhook policy and is similar to the response in [Get a single webhook policy](../webhook_policies.html#get-a-single-webhook-policy).

## Delete a webhook policy

```
DELETE /webhook_policies/:id
```

### Response

```
status: 204 No Content
```

The response contains no body.

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the webhook profile was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the webhook policy may no longer be related to webhooks.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the webhook policy.

jwt\_alg
: *Required* **[enum](../general/enumerations/index.html)** — The JWT algorithm field is used to select the algorithm to use for cryptographic signing of webhook messages. If cryptographic signing is used, the algorithm for decoding a received message needs to be specified to ensure that an attacker cannot bypass the algorithm verification step. See also [JSON Web Algorithms (JWA)](https://tools.ietf.org/html/rfc7518#section-3.1). Valid values are:
: - `none`: No digital signature or MAC performed
 - `hs256`: HMAC using SHA-256
 - `hs384`: HMAC using SHA-384
 - `hs512`: HMAC using SHA-512
 - `rs256`: RSA using SHA-256
 - `rs384`: RSA using SHA-384
 - `rs512`: RSA using SHA-512
 - `es256`: ECDSA using P-256 and SHA-256
 - `es384`: ECDSA using P-384 and SHA-384
 - `es512`: ECDSA using P-521 and SHA-512

jwt\_audience
: *Optional* **[text](../general/data_types.html) (max 2KB)** — The Audience field is used to specify the value for the audience claim. The audience claim identifies the recipients that the encrypted message is intended for. For more information see [“aud” (Audience) Claim](https://tools.ietf.org/html/rfc7519#section-4.1.3) of a JSON Web Token (JWT).

jwt\_claim\_expires\_in
: *Optional* **[duration](../general/data_types.html)** — The Claim expires in field is used to specify the expiration time on or after which the JSON Web Token (JWT) must no longer be accepted for processing. The payload of a webhook will have an “exp” (expiration time) claim based on this value. The processing of the “exp” claim requires that the current date/time must be before the expiration date/time listed in the “exp” claim. Implementers may provide for some small leeway, usually no more than a couple of minutes, to account for clock skew. For more information see [“exp” (Expiration Time) Claim](https://tools.ietf.org/html/rfc7519#section-4.1.4) of a JSON Web Token (JWT).

name
: *Readonly* **[string](../general/data_types.html) (max 64)** — The Name field contains the generated name of the policy.

public\_key\_pem
: *Readonly* **[text](../general/data_types.html) (max 2KB)** — The public\_key\_pem field contains the public key of the created policy. This field is only available when a new policy is created.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the webhook policy. If the policy has no updates it contains the `created_at` value.
