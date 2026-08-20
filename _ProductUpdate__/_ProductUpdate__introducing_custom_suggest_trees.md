---
title: "Introducing Custom Suggest Trees"
date: "October 7, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-custom-suggest-trees"
slug: "introducing-custom-suggest-trees"
---

# Introducing Custom Suggest Trees

Custom suggest fields can be added to UI extensions when it is necessary to ask users to select a value from a list of organization-specific options.  Now it is possible to create dependencies between such lists.  When a user selects an option from the first custom list, this limits the options of the second list, and so on.  This creates tree-like structures; the ‘Custom Suggest Trees’.

As an example, let’s consider an organization that has several sites, consisting of multiple buildings.  To enable users to select a specific room in a request, he or she would ideally select a site, then a building from that site, and then a room from that building.  So far, this would only be partly possible.  Sites already exist in Xurrent, so the account designer can create two custom collections: ‘Buildings’ and ‘Rooms’.  The ‘Buildings’ collection has a UI extension with a filterable site suggest field.  The ‘Rooms’ collection has a UI extension with a custom suggest field.

Each custom collection has its own set of custom collection elements (every building and every room), and for each custom collection a custom view is created to make these elements available for selection in a custom suggest field in a UI extension within a request template.  These steps are described in a previous [blog post about custom collections](https://www.xurrent.com/product-updates/introducing-custom-collections).  So far, a user could select a site, and subsequently choose a building from a custom list, filtered on the selected site.

Now it is possible to take this one step (or several steps) further.  When adding a custom suggest field to a UI extension via the HTML snippets, an account designer can add a filter to create a dependency on another custom suggest field in the UI extension.  This way, custom suggest trees can be created with several branch levels.

For our example, a third UI extension is made, containing a site suggest field for selecting the site, a custom suggest field for selecting the building and another custom suggest field for selecting the room.

The HTML code for the UI extension snippets now looks like this:

From the interface, to be placed in a request template, the user would be able to create a custom suggest tree starting from a site and then branching off to a building and a room.

