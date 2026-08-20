# PDF Designs API

- [List PDF Designs](index.html#list-pdf-designs)
- [Get a single PDF Design](index.html#get-a-single-pdf-design)
- [Create a PDF Design](index.html#create-a-pdf-design)
- [Update a PDF Design](index.html#update-a-pdf-design)
- [Fields](index.html#fields)

## List PDF Designs

List all PDF Designs for an account:

```
GET /pdf_designs
```

### Response

```
status: 200 OK
```

```
[{"id":14,"sourceID":null,"name":"Default Dashboard","category":"dashboard","disabled":false,"created_at":"2023-08-31T08:21: 04-05: 00","updated_at":"2023-08-31T08:21: 04-05: 00","nodeID":"..."},{"id":13,"sourceID":null,"name":"Default Project Summary","category":"project_summary","disabled":false,"created_at":"2023-08-31T08:21: 04-05: 00","updated_at":"2023-08-31T08:21: 04-05: 00","nodeID":"..."},{"id":12,"sourceID":null,"name":"Default Workflow Summary","category":"workflow_summary","disabled":false,"created_at":"2023-08-31T08:21: 04-05: 00","updated_at":"2023-08-31T08:21: 04-05: 00","nodeID":"..."}]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of PDF Designs.

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of PDF Designs:

`id` `sourceID` `category` `created_at` `name` `disabled` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `disabled` `category`

### Sorting

By default a collection of PDF Designs is sorted **ascending** by `created_at`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `created_at` `updated_at`

## Get a single PDF Design

```
GET /pdf_designs/:id
```

### Response

```
status: 200 OK
```

```
{"category":"workflow_summary","created_at":"2023-08-31T08:21:04-05:00","css":"...","disabled":false,"html":"...","id":12,"name":"Default Workflow Summary","source":"4me","sourceID":"213asdad","updated_at":"2023-09-05T02:29:37-05:00","nodeID":"..."}
```

The response contains [these fields](index.html#fields).

## Create a PDF Design

```
POST /pdf_designs
```

When creating a new PDF Design [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created PDF Design and is similar to the response in [Get a single PDF Design](index.html#get-a-single-pdf-design)

## Update a PDF Design

```
PATCH /pdf_designs/:id
```

When updating a PDF Design [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"created_at":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated PDF Design and is similar to the response in [Get a single PDF Design](index.html#get-a-single-pdf-design)

## Fields

category
: *Required* **[enum](../general/enumerations/index.html)** — The design category that was selected when the PDF design was created. Valid values are:

 - `dashboard`: Dashboards
 - `project_summary`: Project Summaries
 - `workflow_summary`: Workflow Summaries

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the PDF Design was created.

css
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The CSS field is used to maintain the CSS code of the PDF design.

description
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Description field is used to describe the PDF design.

description\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Description field.

disabled
: *Optional* **[boolean](../general/data_types.html)**, default: `false` — The Disabled box is checked when the design may no longer be used, for instance in approval tasks or dashboards.

html
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The HTML field is used to maintain the HTML code of the PDF design.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the PDF Design.

name
: *Required* **[string](../general/data_types.html) (max 128)** — The Name field is used to enter a name for the PDF design.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the PDF Design. If the PDF Design has no updates it contains the `created_at` value.
