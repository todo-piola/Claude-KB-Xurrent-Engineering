---
title: "Change Approval Rejection Count"
date: "April 19, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/change-approval-rejection-count"
slug: "change-approval-rejection-count"
---

# Change Approval Rejection Count

Thanks to the suggestion of one of Xurrent’s larger enterprise customers, a new hidden field called ‘Rejection count’ has been added to change approval tasks.  This field counts the number of times a change task has been updated to the status ‘Rejected’.

Organizations can use this field in multiple ways.  For example, they can use it to look up approval tasks that have been rejected more than once.  Or they can use it to check whether tasks that are based on certain approval task templates get rejected more often than approval tasks based on other templates.  It might even be useful to check whether some approvers have rejected a large number of approval tasks, which might indicate that this approver expects changes to be planned more thoroughly before approval is requested.

The Rejection count field is similar to the [Assignment count field](https://www.xurrent.com/product-updates/assignment-count) and the [Reopen count field](https://www.xurrent.com/product-updates/reopen-count) of requests.  The value in all three of these fields can be retrieved using the [Xurrent GraphQL API](https://developer.xurrent.com/graphql/), as well as the [Xurrent REST API](https://developer.xurrent.com/v1/).  The queries below provide an example for the Rejection count field using each of these APIs.

**GraphQL API**

`query getTasks {
tasks
last: 5, filter:{query:"approval"}) {
totalCount
nodes{
id
rejectionCount
}
}
}`

**REST API**

`$ curl -i -H "Authorization: Bearer oT9b…ci6Y" -H "X-4meAccount: wdc" -X GET "https://api.4me.com/tasks?fields=id,subject,rejection_count"`
