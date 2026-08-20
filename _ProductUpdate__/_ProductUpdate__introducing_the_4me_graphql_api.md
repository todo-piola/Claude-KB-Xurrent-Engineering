---
title: "Introducing the Xurrent GraphQL API"
date: "September 21, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-the-4me-graphql-api"
slug: "introducing-the-4me-graphql-api"
---

# Introducing the Xurrent GraphQL API

Developers within the Xurrent community will be excited to hear that the Xurrent GraphQL API has been released.  Like [Xurrent’s REST API](https://developer.xurrent.com/v1/), this new API can be used to retrieve and update Xurrent data.  The reason why developers like GraphQL so much, though, is its efficiency.  It allows developers to be more specific so they’ll get a more precise result with a single API request.

For example, if Xurrent’s REST API is used to look up the address of the site where someone’s manager works, multiple API requests are needed.  The first API call looks up the person record of the individual whose manager’s site address needs to be retrieved.  This returns all data of this person record.  From this data, the person ID of the manager is obtained and this ID is then used for the second API request, which retrieves all data of the manager’s person record.  From this record the Site ID is collected, which is then used to retrieve the data of the site record in a third API request.  The last step is to extract the address of the site from the site data.

That is three API requests and quite some data retrieved only to get the address of a site.  Because Xurrent’s REST API is very fast, this does not really slow down integrations, but it would be easier if developers could use a single API request to only obtain the address of the site of the manager of a specific individual.

That is the capability this new GraphQL API brings to the table.  It speeds up the development of integrations, which is great for developers.  Because it can also dramatically reduce the number of queries needed for an integration, this realizes significant cost savings for organizations relying on integration platforms that charge per API request.

The GraphQL query language allows developers to define what they need in a JSON (JavaScript Object Notation) object and to send this over HTTP after which the response is returned in JSON.  The functionality of a GraphQL API is described by its schema.  Every GraphQL schema has a root type for queries (for retrieving data) and mutations (for adding, updating and deleting data).  The [Xurrent Developer website](https://developer.xurrent.com/graphql/) has been updated to help developers get started with the Xurrent GraphQL API.
