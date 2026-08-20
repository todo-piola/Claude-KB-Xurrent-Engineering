# Project Templates API

- [List project templates](index.html#list-project-templates)
- [Get a single project template](index.html#get-a-single-project-template)
- [Create a project template](index.html#create-a-project-template)
- [Update a project template](index.html#update-a-project-template)
- [Fields](index.html#fields)

## List project templates

List all project templates for an account:

```
GET /project_templates
```

### Response

```
status: 200 OK
```

```
[{"id":456,"sourceID":null,"subject":"Large project phases","created_at":"2016-12-23T05:09:05-06:00","updated_at":"2016-12-23T05:09:05-06:00"},{"id":448,"sourceID":null,"subject":"Medium project phases","created_at":"2016-12-23T05:09:05-06:00","updated_at":"2016-12-23T05:09:05-06:00"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of project templates.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/project_templates/disabled`: List all disabled project templates
- `/project_templates/enabled`: List all enabled project templates

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of project templates:

`id` `sourceID` `subject` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `subject` `disabled` `created_at` `updated_at`

### Sorting

By default a collection of project templates is sorted **descending** by `id`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `subject` `created_at` `updated_at` `times_applied`

## Get a single project template

```
GET /project_templates/:id
```

### Response

```
status: 200 OK
```

```
{"created_at":"2016-12-23T05:09:05-06:00","disabled":false,"id":456,"source":null,"sourceID":null,"subject":"Large project phases","times_applied":8,"updated_at":"2016-12-23T05:09:05-06:00"}
```

The response contains [these fields](index.html#fields).

## Create a project template

```
POST /project_templates
```

When creating a new project template [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created project template and is similar to the response in [Get a single project template](index.html#get-a-single-project-template)

## Update a project template

```
PATCH /project_templates/:id
```

When updating a project template [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"category":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated project template and is similar to the response in [Get a single project template](index.html#get-a-single-project-template)

## Fields

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the project template was created.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the project template may not be used to help register new projects.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the project template.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

subject
: *Required* **[string](../general/data_types.html) (max 190)** — The Subject field is used to enter a short description that needs to be copied to the Subject field of a new [project](../projects/index.html) when it is being created based on the template.

times\_applied
: *Readonly* **[integer](../general/data_types.html)** — The number of times the project template is used to create a project.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the project template. If the project template has no updates it contains the `created_at` value.
