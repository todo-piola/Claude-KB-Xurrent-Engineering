# Pagination

API requests that return collections of records are always paginated.
The default page size of 20 records can be adjusted by setting the `?per_page=` parameter.
The maximum number of records per page is 100.

Use the [Link Header](../pagination.html#link-header) to browse through the pages of the result.

```
$ curl https://api.xurrent.com/v1/requests?per_page=25&search_after=eyJvZmZzZXQiOjUsImN1cnNvciI
```

Pagination information will be returned in the response header.

```
x-pagination-per-page: 25
x-pagination-current-page: 3
x-pagination-total-pages: 10
x-pagination-total-entries: 243
```

## Link Header

Use the [the Link header](http://www.w3.org/Protocols/9707-link-header.html) to browse through the pages of the result:

```
link: <https://api.xurrent.com/v1/requests?per_page=25>; rel="first",
 <https://api.xurrent.com/v1/requests?per_page=25&search_before=IicvNnc1NmIsUjOiQXZzZmZvJye>; rel="prev",
 <https://api.xurrent.com/v1/requests?per_page=25&search_after=eyJvZmZzZXQiOjUsImN1cnNvciIx>; rel="next"
```

The possible `rel` values are:

first
: Shows the URL of the first page of results. This value is present in the Link header of all pages, except the first.

prev
: Shows the URL of the immediate previous page of results. This value is present in the Link header of all pages, except the first.

next
: Shows the URL of the immediate next page of results. This value is present in the Link header of all pages, except the last.

## Throttling

In some cases, most notably the [Audit Entries](../../audit_entries.html) and [Notes](../../notes.html) APIs,
the maximum number of records that can be retrieved as a single collection of pages is limited to 100.000 records.
When more than 100.000 records are found by an API request, the following is included in the HTTP Response Header:

```
x-pagination-throttled: true
```
