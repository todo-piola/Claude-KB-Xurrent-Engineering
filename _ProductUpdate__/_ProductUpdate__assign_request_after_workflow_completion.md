---
title: "Assign Request After Workflow Completion"
date: "February 14, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/assign-request-after-workflow-completion"
slug: "assign-request-after-workflow-completion"
---

# Assign Request After Workflow Completion

Sometimes, when an approval is needed for a request, users want to continue working on that request after that approval.  Until now, the work would have to continue on a workflow, as approval tasks are part of a workflow.  When in a request template in edit mode a workflow template is selected, the fields Team, Member and Supplier from the ‘Assignment’ section are hidden and the Workflow manager field is shown.  Creating a request from such a request template would start a workflow that, once completed, completes the original request as well.  A new option has now been added that makes it possible to reassign the request to a team (or a specific member of a team) after the selected workflow has been completed.

Consider a situation where two request templates exist:

1. give a user access to Application X
2. give a user access to Application Y.

Both service requests first require an approval.  The current way to handle this would be to also have two change templates, with two tasks each.  The first task is the shared approval task, and the second task is the actual implementation task, which is usually assigned to a different team and contains different instructions.

To make this process more efficient without making the approval a part of the request – and with that having to build every current and future workflow capability into requests – the ‘Assign after workflow completion’ option is introduced.  When checking this option, the Team and Member fields become available again.  After the workflow has been completed, the request is then assigned to this team or member, to perform the necessary action (giving access to an application, in this example).  This way, a single approval workflow can be created that can be used in many request templates.

