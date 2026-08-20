# Request Satisfaction API

- [Requester is satisfied](../satisfaction.html#requester-is-satisfied)
- [Requester is dissatisfied](../satisfaction.html#requester-is-dissatisfied)

The following is required for this API to work:

- the request must have status `Completed`
- the request was completed in the last `<x>` days
- the authenticated user is either the Requested By or the Requested For person of the request
- the authenticated user did not already indicate his/her satisfaction since the last time the request was completed

When the satisfaction indication is successfully updated the response status will be 204 (“No Content”), otherwise it will be 304 (“Not Modified”).

The value of `<x>` can be configured by account administrators via the Reopen requests and Provide feedback fields
on the Self Service Settings form.

## Requester is satisfied

Indicates that the authenticated user is satisfied with the manner in which the given request has been handled.

```
POST /requests/:id/satisfied
```

### Response

```
status: 204 No Content
```

## Requester is dissatisfied

Indicates that the authenticated user is dissatisfied with the manner in which the given request has been handled.

```
POST /requests/:id/dissatisfied
```

note
: *Required* **[text](../../general/data_types.html) (max 64KB)** — The Note field is used to provide any additional information that could prove useful for resolving the request.

note\_attachments
: *Optional* **aggregated** — Attachments to the note.

reopen
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` — Set to the value `true` if the user wants to reopen the request.

### Response

```
status: 204 No Content
```
