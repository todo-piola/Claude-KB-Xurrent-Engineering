# Project Categories API

- [List project categories](index.html#list-project-categories)
- [Get a single project category](index.html#get-a-single-project-category)
- [Create a project category](index.html#create-a-project-category)
- [Update a project category](index.html#update-a-project-category)
- [Fields](index.html#fields)

## List project categories

List all project categories for an account:

```
GET /project_categories
```

### Response

```
status: 200 OK
```

```
[{"id":2,"sourceID":null,"reference":"small","name":"Small","description":"Less than 50 workdays and $50K","position":1,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"},{"id":3,"sourceID":null,"reference":"medium","name":"Medium","description":"Less than 200 workdays and $200K","position":2,"created_at":"2016-12-23T05:09:03-06:00","updated_at":"2016-12-23T05:09:03-06:00"}]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of project categories.

### Collection Fields

By default the following fields will appear in collections of project categories:

`id` `sourceID` `reference` `name` `description` `position` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields=parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `disabled` `reference` `name` `created_at` `updated_at`

The filters on `source`, `sourceID`, `reference` and `name` are not case sensitive.

### Sorting

By default a collection of project categories is sorted **ascending** by `id`.

The following fields are accepted by the [?sort=parameter](../general/ordering.html):

`id` `sourceID` `reference` `name` `position` `created_at` `updated_at`

## Get a single project category

```
GET /project_categories/:id
```

### Response

```
status: 200 OK
```

```
{"attachments":[],"created_at":"2016-12-23T05:09:03-06:00","description":"Less than 50 workdays and $50K","disabled":false,"id":2,"information":"A small project is not expected to exceed either of the following thresholds:\n\n* Internal effort: 50 workdays\n* Cost of purchases (including cost of external effort): $50K","name":"Small","position":1,"reference":"small","source":null,"sourceID":null,"updated_at":"2016-12-23T05:09:03-06:00"}
```

The response contains [these fields](index.html#fields).

## Create a project category

```
POST /project_categories
```

When creating a new project category [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created project category and is similar to the response in [Get a single project category](index.html#get-a-single-project-category)

## Update a project category

```
PATCH /project_categories/:id
```

When updating a project category [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"id":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated project category and is similar to the response in [Get a single project category](index.html#get-a-single-project-category)

## Fields

attachments
: *Readonly* **aggregated Attachments**

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the project category was created.

description
: *Optional* **[string](../general/data_types.html) (max 255)** — The Description field is used to enter a very short description of the project category, for example “More than 200 workdays or $200K”.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the project category may not be related to any more projects.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the project category.

information
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Information field is used to add any additional information about the project category that might prove useful, especially for project managers when they need to decide which project category to select for a project.

information\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Information field.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter the name of the project category. Ideally the name of a project category consists of a single word, such as “Large”.

position
: *Optional* **[integer](../general/data_types.html)** — The Position field dictates the position that the project category takes when it is displayed in a sorted list.

reference
: *Readonly* **[string](../general/data_types.html) (max 128)** — The Reference field is automatically set to the Name field value, written in lower case characters and with all spaces replaced by the underscore character. This reference can be used to link the project category to a project using the Xurrent REST API or the Xurrent Import functionality.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the project category. If the project category has no updates it contains the `created_at` value.
