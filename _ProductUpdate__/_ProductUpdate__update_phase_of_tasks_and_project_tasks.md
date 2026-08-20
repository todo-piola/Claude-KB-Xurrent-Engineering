---
title: "Update Phase of Tasks and Project Tasks"
date: "March 22, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/update-phase-of-tasks-and-project-tasks"
slug: "update-phase-of-tasks-and-project-tasks"
---

# Update Phase of Tasks and Project Tasks

Since last week it is possible to [dynamically add tasks to a workflow](https://www.xurrent.com/product-updates/add-tasks-to-workflows-dynamically).  This can be done with the help of [automation rules](https://help.xurrent.com/help/automation_rule/).  This functionality has now been expanded somewhat.  It is now also possible to determine the phase of the workflow to which a task should belong, and the phase of a project to which a project task should belong.

For a workflow, phases can be created by a workflow manager from the Gantt chart of the workflow or the workflow template.  The use of phases is useful to get a good overview of the progress of a workflow or of a project.

In the example below, a workflow phase has been created in which canceled tasks are to be placed.  An automation rule is created for a task that moves it to the ‘Canceled Tasks’ phase as soon as it is canceled.  This approach can lead to a much better overview of the workflow, especially in the workflow management of an organization that often involves tasks that are subsequently canceled.

The `Phase_name` field is not only available for tasks, but also for project task records in automation rules.
