# Waiting for Customer Follow-Ups - Waiting for Customer Rules API

## List all waiting for customer rules of a waiting for customer follow-up

List all waiting for customer rules of a waiting for customer follow-up with a specific ID.

```
GET /waiting_for_customer_follow_ups/:id/waiting_for_customer_rules
```

### Response

```
status: 200 OK
```

```
[{"id":1,"nr_of_business_days":7,"created_at":"2022-11-24T18:39:44-06:00","updated_at":"2022-11-24T18:39:44-06:00"},{"id":2,"nr_of_business_days":14,"created_at":"2022-11-24T18:39:44-06:00","updated_at":"2022-11-24T18:39:44-06:00"}]
```

The response contains [these fields](index.html#fields) by default.

## Add a waiting for customer rule to a waiting for customer follow-up

Add a new waiting for customer rule to a waiting for customer follow-up with a specific ID.

```
POST /waiting_for_customer_follow_ups/:id/waiting_for_customer_rules
```

When adding a new rule to a waiting for customer follow-up [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{}
```

## Remove a waiting for customer rule from a waiting for customer follow-up

Remove the link between a waiting for customer follow-up with a specific ID and a waiting for customer rule with a specific ID.

```
DELETE /waiting_for_customer_follow_ups/:id/waiting_for_customer_rules/:rule_id
```

### Response

```
status: 204 No Content
```

## Remove all waiting for customer rules from an waiting for customer follow-up

Remove all links between a waiting for customer follow-up with a specific ID and its waiting for customer rules.

```
DELETE /waiting_for_customer_follow_ups/:id/waiting_for_customer_rules
```

### Response

```
status: 204 No Content
```

## Fields

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the waiting for customer rule was created.

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the waiting for customer rule.

nr\_of\_business\_days
: *Required* **[integer](../../general/data_types.html)** — The number of business days to wait before a notification should be generated.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the waiting for customer rule. If the waiting for customer rule has no updates it contains the `created_at` value.
