---
title: "Introducing the Xurrent Shop"
date: "December 20, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-the-4me-shop"
slug: "introducing-the-4me-shop"
---

# Introducing the Xurrent Shop

A much-requested and major new feature has been added to Xurrent: the Shop capability.  It allows people from the organization (and even their customer organizations) to order items or services directly from the Xurrent Self Service portal.

**Read the full press release**[**here.**](https://www.newswire.com/news/service-management-platform-4me-introduces-a-fully-functional-webshop-21930911)

To properly explain the workings and possibilities of the webshop feature, this article is split up into three sections:

1. Setting Up the Shop
2. Creating Shop Articles
3. Ordering and Fulfillment

**1. Setting Up the Shop**

To set up the shop, two specific request templates are needed (one for the entire order, and one for the individual order lines) and one specific workflow template.

The first step is to create a workflow template of the (new) category ‘Order’, related to a service.  This workflow includes a ‘Fulfillment Placeholder’ task template, which Xurrent automatically creates if it does not exist yet.  When this placeholder task is assigned, generally after a prior approval task has been approved, the placeholder is replaced by a fulfillment task for each ordered shop article.  The screenshot below shows an Order workflow for the Personal computing service, with a single approval task and the Fulfillment Placeholder task.

This screenshot, just as the other screenshots used in this article, is taken from the Demo environment, which already includes a working shop.  This should make it easier for organizations to already familiarize themselves with the configuration and possibilities.

The next step is to create the first of the two request templates.  This template must be of category ‘Order’, and it must be related to the workflow template of the first step.  This request template defines which organizations have access to the shop.  Mind that each organization therefore may only be related to one request template of category ‘Order’.  This template generates a request for purchase, which can include multiple articles, when an order is placed.

The order request template would also be a good place to add a UI extension, when it is important for a purchaser to specify a cost center, for example.

How the shop-related templates are connected is visualized in the chart below.

The second request template that must be created to set up the shop is of another newly introduced category: ‘Fulfillment’.  This template is used to generate fulfillment requests for every shop article that was ordered in the request for purchase.  This is done by automatically generating a request from each task created by the Fulfillment Placeholder task template.  In the Fulfillment request template the team (and possibly the member of the team) that needs to take care of the order fulfillment can be selected.

**2. Creating Shop articles**

What is a shop without articles? The articles that your users can purchase can be defined in the ‘Shop Articles’ section of the Records console.

Next to some general information about an article itself, its shop attributes are defined in the sections for pricing, fulfillment, availability, and service offerings.

The price can be set as a fixed amount, or as a recurring amount; either monthly or yearly.  This also makes the shop suitable for charging for services, or leasing equipment, for example.

The ‘Fulfillment’ section is where the fulfillment request template is selected and where information about shipping and delivery is gathered.  Here, a UI extension may also be added, in this example to let the purchaser select the color of a mouse.

One of Xurrent’s strong features is its architecture, which allows for easy and seamless integration between accounts.  This is also true for the shop feature.  When an organization creates a shop article and relates that to a service offering for which an active SLA with an external customer exists, users of that customer account are also able to purchase this article.  That customer is even able to change the name, descriptions, pricing, and other fields.  If a field is updated, the new value overrides the original.  If not, the original value is kept.  This way, it is possible to rebrand products and services from a provider, or just simply change the prices.  In the example below, only the original full description is maintained equal.

Shop articles that have been made available to external customers are disabled in the account of the customer by default.  To be made available for their users, the customer needs to enable them first.

**3. Ordering Articles**

If setting up the shop and articles is already very straightforward; ordering is even easier.  In Xurrent Self Service, two new menu options are now available: one for ordering articles, and one for viewing previously made orders.  Selecting the ‘Shop’ option will take the end user to the shop page.

After selecting an article and adding the required quantity to the cart, the user is guided to the ‘Checkout’ page, where a summary of the order is given before the **Order**button can be pressed.  After that, the Order workflow is started.

Specialists can follow the status of individual articles for which the purchasing process has started in the new ‘Shop Order Lines’ section of the Records console.  These statuses can be either: `In Cart`, `Workflow Pending`, `Fulfilment Pending`, `Completed`, or `Canceled`.

The complete flow from a purchase (in this example of two articles) to its fulfillment can be summarized as follows:

