# Search API

The Search API is used to perform searches through the most relevant Xurrent records for the API’s user. It searches for:

- requests that were requested by or for the API user
- workflow approval tasks assigned to the API user
- project tasks assigned to the API user
- services for which the API user is covered by an active SLA
- service instances belonging to services for which the API user is covered by an active SLA
- request templates related to services for which the API user is covered by an active SLA
- knowledge articles related to services for which the API user is covered by an active SLA
- configuration items that belong to the API user

## Search

Perform a search query:

```
GET /search?q=conference
```

The search query can be provided using the `q` parameter.

### Response

```
status: 200 OK
```

```
[{"id":18,"type":"service","title":"Conference Room","details":"The Conference Room service provides telephone conferencing and projection capabilities in the meeting rooms of the Widget Data Center organization.","url":"https://api.itrp-demo.com/v1/services/18","avatar_url":"https://itrp-demo-defaults.s3-accelerate.dualstack.amazonaws.com/avatars/services/original/presentation1.svg"},{"id":4,"type":"request-template","title":"Extension of service hours for the Conference Room service","details":"Determine the period during which the selected service needs to be available and supported, even though these hours are not covered by the current SLA.\nSpecify the period between which the service needs to be available and supported using the Start and End…","url":"https://api.itrp-demo.com/v1/request_templates/4"}]
```

The response contains a collection of results. Each result contains [these fields](index.html#fields). [Filtering](index.html#filtering) and [pagination](index.html#pagination) are available to reduce/limit the collection of sites.

### Fields

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the result.

type:
: *Readonly* **[string](https://developer.xurrent.com/v2/general/data_types/)** — The type of the result. Valid values are:

 - `ci`
 - `knowledge-article`
 - `project-task`
 - `request`
 - `request-template`
 - `service`
 - `service-instance`
 - `task`

title
: *Readonly* **[string](../general/data_types.html)** — The subject or name of the result.

details
: *Optional* **[string](../general/data_types.html)** — The extra details about the result, different for each type:

 - `knowledge-article`: the description or (if empty) instructions
 - `request`: the last note
 - `service`: the description

url
: *Readonly* **[string](../general/data_types.html)** — The URL to the details of the result.

avatar\_url
: *Optional* **[string](../general/data_types.html)** — The URL to the uploaded avatar.

## Sorting

The results are always sorted by **relevance**.

## Filtering

The scope of a search request can be reduced by passing one or more filter
conditions:

```
$ curl https://api.xurrent.com/v1/search?q=unix&types=req,request-template
```

The following operators can be used in filter conditions:

types
: If specified, limits the results to those record types. Possible values:

 - `ci`
 - `knowledge-article`
 - `project-task`
 - `request`
 - `request-template`
 - `service`
 - `service-instance`
 - `task`

 `?types=req,task` or `?types=request-template`

on\_behalf\_of
: When this filter condition is specified, the Search API performs the search on
 behalf of the person whose ID or primary email address is specified. The
 results of a search on behalf of someone else are restricted to the services,
 request templates and knowledge articles for which this other person is
 covered by an active SLA.

 In case two or more person records with the same primary email address exist in
 different Xurrent accounts, specify the ID rather than the primary email address to
 uniquely identify the person record.

## Pagination

Search API requests are always paginated. The default page size of 25 records
can be adjusted by setting the `?per_page=` parameter. The maximum number of
records per page is 100.

If the result of a search query contains more records than the `?per_page=`
parameter, the response will contain the `x-pagination-next-page` header. This
header contains a unique token that can be used as the `?page=` parameter to
retrieve the next page.

For example, the following cURL command searches for ‘windows’ using a page
size of 2:

```
$ curl https://api.xurrent.com/v1/search?per_page=2&q=windows
...
x-pagination-next-page: 9c6921aced7dfb66db958b4d9e2cd4ee
x-pagination-per-page: 2
link: <https://api.xurrent.com/search?per_page=2&q=windows&page=9c6921aced7dfb66db958b4d9e2cd4ee>; rel="next"
...
[
 {
 "title": "Windows password reset required",
 "details": "",
 "id": 114,
 "type": "request-template",
 "url": "https://api.xurrent.com/v1/request_templates/114"
 },
 {
 "title": "How to customize the Windows 10 Start menu",
 "details": "The Start menu is back in Windows 10 by popular demand. You are likely to spend quite a bit of time with the Start menu. Whether you are using it in the more traditional Windows way, or using Cortana to search for content on your PC or the web, it is impor…",
 "id": 10,
 "type": "knowledge-article",
 "url": "https://api.xurrent.com/v1/knowledge_articles/10"
 }
]
```

The `x-pagination-next-page` token can be used to retrieve the next page as follows:

```
$ curl https://api.xurrent.com/v1/search?page=9c6921aced7dfb66db958b4d9e2cd4ee&per_page=2&q=windows
...
```

The `x-pagination-per-page` token remains valid for 30 minutes.

The relevance score of a search result, which is used for sorting, is somewhat non-deterministic.
In some cases, a search result that has already been listed on a previous page may re-occur on a later page.

If it is important for your application that search results are unique, we recommend you to keep track
of search results that have already been listed and filter out duplicates.
