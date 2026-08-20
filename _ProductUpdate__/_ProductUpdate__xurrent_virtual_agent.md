---
title: "Xurrent Virtual Agent"
date: "February 3, 2025"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/xurrent-virtual-agent"
slug: "xurrent-virtual-agent"
---

# Xurrent Virtual Agent

We are excited to announce the release of the Xurrent AI powered Virtual Agent!  In line with our previous usage of AI we are targeting practical workflow improvements for our users.  The Virtual Agent will be available on Self Service and is designed to interact with end users to aid them as they seek assistance.  Our general goal is to give the Virtual Agent a bias towards action.  For example: if the user states: ‘I need a new Oracle database by the end of the year’,  the Virtual Agent immediately opens a ticket and routes it using the ‘AI auto classifier.’

Specifically this new virtual agent will be capable of:

1. Highlighting calls to action
2. Summarizing and returning knowledge articles
3. Registering a new request
4. Reminding the user that a request may already exist
5. Returning details related to degraded services

‍

‍

**(1) Highlighting calls to action.**

If a user has tasks in their inbox, the Virtual agent will summarize and suggest the user take action.  In the example to the right, Howard has three tasks that need his attention:

One completed request for which a satisfaction rating is asked;

One request with status ‘Waiting for Customer’, for which the current user needs to give input;

One approval task.

‍

‍

‍

**(2) Summarizing and returning knowledge articles.**

Sometimes users just want information that is available within the knowledge base:

**(3) Registering a new Request for a user**.

As noted above, we have built in a bias toward action.  So in the example on the right, the user made it clear that they need something quickly. Instead of returning a knowledge article as above, the Xurrent Virtual Agent immediately registers a request for the user:

**(4) Reminding the user that a request may already exist**.

The virtual agent does this by accessing requests within the authenticated users inbox:

As part of the bias toward action, the Virtual Agent is recommended to be used in conjunction with the ‘AI Auto Classifier.’  The goal is to make the interaction with the Virtual Agent fast and efficient.  Thus the Virtual Agent sends in requests to the ‘Other’ category and lets the ‘Auto Classifier’ pick them up and route them appropriately.  Xurrent attempts to fill in fields from the request template based on the conversation where possible.

For example, the above request for an urgent Oracle database above was picked up and automatically sent to the responsible team:

If your organization uses the self-service portal from the directory account – as a lot of organizations do – the Virtual Agent looks across support domains.  One small security improvement added for organizations that have strong privacy enabled is to first ask the user if the agent has selected the proper support domain.  This is designed to prevent sensitive requests from being mis-routed to the wrong support domain. (i.e. an HR issue being sent to the Facilities team.)

**(5) Returning details related to degraded services**.

The virtual agent has access to see if any services in the service catalog are degraded.  This is very useful to help customers coming to the help desk inquiring about an ongoing problem.

To enable the Virtual Agent simply navigate to the ‘Self Service Settings’ section of the Settings console and toggle it on:

Additionally, in the ‘Self Service Design’ section of the Settings console it is possible to determine from which self-service portal the Virtual Agent should be available.

Organizations that use the support chat functionality can continue to do so. In that case, users are able to toggle between the two experiences via the **Talk to Service Desk** but:
