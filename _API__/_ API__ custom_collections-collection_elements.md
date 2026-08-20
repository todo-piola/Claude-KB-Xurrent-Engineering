# Collection Elements - Custom Collections API

## List collection elements of a custom collection

List all [collection elements](../../custom_collection_elements/index.html) of the custom collection with with a specific ID.

```
GET /custom_collections/:id/collection_elements
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"custom_collection":"collection_2","reference":"item_1","name":"Item 1","description":"1st item","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"custom_collection":"collection_2","reference":"item_2","name":"Item 2","description":"Another item","created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"}]
```

The response contains [these fields](../../custom_collection_elements/index.html#collection-fields) by default.

### Predefined Filters

The following [predefined filters](../../general/filtering.html#predefined-filters) are available:

- `/custom_collections/:id/collection_elements/enabled`: List all enabled elements of a custom collection with a specific ID
- `/custom_collections/:id/collection_elements/disabled`: List all disabled elements of a custom collection with a specific ID
