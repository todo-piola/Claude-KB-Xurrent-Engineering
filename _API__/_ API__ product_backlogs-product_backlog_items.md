# Product backlogs - Items API

- [List all items of a product backlog](index.html#list-all-items-of-a-product-backlog)
- [Add/Update/Remove an item to a product backlog](index.html#addupdateremove-an-item-to-a-product-backlog)
- [Fields](index.html#fields)

## List all items of a product backlog

List all items of a product backlog with a specific ID.

```
GET /product_backlogs/:id/product_backlog_items
```

### Response

```
status: 200 OK
```

```
[{"created_at":"2022-03-04T01:09:03-06:00","position":2,"problem":{"id":208,"subject":"Insufficient memory warnings for Sales Tracking Production","nodeID":"..."},"updated_at":"2022-03-04T01:09:03-06:00","...":"..."},"..."]
```

The response contains [these fields](index.html#fields).

## Add/Update/Remove an item to a product backlog

Updating the items on a product backlog is done by setting the `product_backlog_id` and `product_backlog_position` fields of the [requests](../../requests.html) and [problems](../../problems.html) of the items.
By setting the `product_backlog_id` to `null` the request or problem is removed from the product backlog.

## Fields

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the item was created.

estimate
: *Readonly* **[integer](../../general/data_types.html)** — Estimate of the relative size of this item on the product backlog.

position
: *Readonly* **[integer](../../general/data_types.html)** — The Position field is used to specify the position of the item,
 relative to the other items of the product backlog. The top item has position 1.

problem
: *Readonly* **[reference](../../general/data_types.html#references) to [Problem](../../problems.html)** — The Problem field is filled for problems on the product backlog.

request
: *Readonly* **[reference](../../general/data_types.html#references) to [Request](../../requests.html)** — The Request field is filled for requests on the product backlog.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the item.
 If the item has no updates it contains the `created_at` value.
