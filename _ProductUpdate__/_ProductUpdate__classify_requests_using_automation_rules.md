---
title: "Classify Requests Using Automation Rules"
date: "February 24, 2025"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/classify-requests-using-automation-rules"
slug: "classify-requests-using-automation-rules"
---

# Classify Requests Using Automation Rules

The [Xurrent AI Autoclassifier](https://www.xurrent.com/features/ai-service-management-automation) has proven to be very useful when an end user registers a request without selecting a Service Instance. By selecting ‘None of the Above’ the category is set to ‘Other’ by default. When requests are logged in this manner and the status of the request is ‘Assigned’, a ‘Nearest Neighbors’ search is started, attempting to find a similar request that was previously registered. If the level of confidence of the AI for this classification is high enough, It then classifies: Service Instance, Team, Category, and Impact.

There are, of course, other scenarios where auto-classification would be useful. Requests may come in via an observability integration directly to a specific service instance. It’s also possible that a customer may want to have the AI classification run at different points in time. For example, if a request has been misrouted manually. Now, organizations can set up automation rules to help classify requests, using the new ‘ai_similar_request’ expression.

