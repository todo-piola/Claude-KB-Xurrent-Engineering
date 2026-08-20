---
title: "Make Change Progress Visible in Self Service"
date: "May 6, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/make-change-progress-visible-in-self-service"
slug: "make-change-progress-visible-in-self-service"
---

# Make Change Progress Visible in Self Service

Many customers have asked to make it possible for requesters to track the progress of their requests, even when they are linked to a change.  Such requests would only show the requester that the status is ‘Change Pending’ as long as the workflow of the related change still had unfinished tasks.

This was not very informative.  That is why the Workflow Progress Tracker has been built.  This progress tracker is presented at the top of any open request that is linked to a change that has not yet been completed.

The information the Workflow Progress Tracker provides is also useful for service desk analysts and specialists.  That is why it is presented above requests in the Xurrent Specialist Interface as well.

Change managers can decide which phases are presented in the progress tracker by adding these phases to their changes and change templates.  By default, every change and every change template opens with an empty phase that does not actually exist in the database.  This phase is therefore ignored when the Workflow Progress Tracker presents the phases above a request.

Change managers can add actual phases in the Gantt chart using the ‘Add Phase…’ option, just like project managers do for their projects and project templates.  Once a change manager has added actual phases with names, the tasks or task templates can be dragged to these phases.  When all tasks or task templates have been moved to a phase with a name, the empty phase automatically disappears.

To help organizations establish a consistent naming convention for their change phases, change managers are offered a list of phase names that are used in change templates when they add a new phase to a change or change template.

Because end users will see the phase names, the name of every phase that is specified in a change template can be translated in the ‘[Translations](https://www.xurrent.com/product-updates/filter-translations-by-record-type-and-field)‘ section of the Settings console.

The import/export functionality for change templates, changes, and tasks has been updated as well to include phases.  When the change templates and changes do not have any phases yet, the only thing that has changed is that their export files now have an extra column called ‘Phases’.  Likewise, the column ‘Phase’ has been added to the export files of tasks.

If phases have been added to a change template, the export file includes the name of the phase that a task template is part of after the subject of the task template.  The task template subject and phase name are separated by a**`/`**in the change templates export file.

