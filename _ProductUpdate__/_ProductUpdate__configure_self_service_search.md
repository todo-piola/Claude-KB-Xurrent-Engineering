---
title: "Configure Self Service Search"
date: "March 11, 2025"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/configure-self-service-search"
slug: "configure-self-service-search"
---

# Configure Self Service Search

Until now, the [self-service](https://www.xurrent.com/features/self-service-portal) search results would by default include any results from the following record types, depending on the availability of these record types for the user who is logged in:

- Standard Service Requests
- Knowledge Articles
- Services
- Requests
- Problems
- Tasks
- Project Tasks
- Workflows
- Project
- Shop Articles
- Assets (Configuration Items)

For most organizations and their end users, though, standard service requests and knowledge articles are more important than any of those other results. For other end users, configuration items or services may be more important. They were already able to change the results by pressing the **Refine Search** button, but only after the search.

That is why the self-service search has now been made configurable. An account administrator or account designer can configure the default record types that can come up in self-service search in the ‘Self Service Design’ section of the Settings console, after which the end user is still able to refine the search. Depending on how the self-service portal has been designed, the homepage can contain two types of search fields. Both can be configured independently.

Let’s configure these two search fields to by default limit the global search field in the top bar to just Standard Service Requests, Knowledge Articles and Services, and the search bar to just show Assets.

In the ‘HTML’ section of the Self Service Design look for the search element with class `global-user-menu-btn global-search-link` and change the `href` attribute to:

/self-service/search?types=request-template,knowledge-article,service

It will then look like this:

<a class=”global-user-menu-btn global-search-link” title=”Search” href=”/self-service/search?types=request-template,knowledge-article,service”>

To configure the search bar, look for an element called `self-service-search`. We can change it as follows:

<self-service-search data-placeholder=”Search assets” data-types=”ci”> </self-service-search>

Searching for ‘Emal’ from the top will now only show standard service requests, knowledge articles, and services. Pressing the **Refine Search** button will show those three record types selected. The user can remove or add record types, which immediately changes the results.

