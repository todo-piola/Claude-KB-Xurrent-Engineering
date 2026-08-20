---
title: "Introducing Scrum"
date: "October 24, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-scrum"
slug: "introducing-scrum"
---

# Introducing Scrum

A major new feature has been added to Xurrent®: Scrum support.  Scrum is a framework within which people can address complex adaptive problems, while productively and creatively delivering products of the highest possible value.

As a placeholder for the different records that are related to Scrum, the ‘Scrum Workspaces’ section has been added to the Records console.  A Scrum workspace consists of a team, a product backlog, and an Agile board, which are closely integrated.  In the example below, a workspace has been created for Application Development.  They work with sprint lengths of two weeks and are currently working on the second sprint.  This example is taken from the Demo data, which has already been created to enable immediate testing of this new functionality.

Below that information, the Burndown chart for the current sprint is displayed.  It shows the amount of (story)points on the vertical axis and the sprint length on the horizontal.  The gray line is the ideal trend, calculated by Xurrent considering the team’s work week.  It starts with the planned points for this sprint (in this case 12) and ends at 0.  The blue line shows the actual progress of the sprint and the red line shows how many points have been added during the sprint (scope creep).  Surely, this was not an ideal sprint, which should probably be discussed during the team’s next sprint retrospective.

Right under the Burndown chart, the ‘Sprints’ section shows the sprints related to this Scrum workspace.  From there, the Burndown charts from the completed sprints can be viewed.  These are mainly for reference.  It is also possible to look at the next (Registered) sprint. Let’s first look at the current (Active) sprint.

Clicking on the Active link brings up the sprint summary, including a few new buttons:

Next to the **Edit**button is the **Show scrum workspace**button and then the current **Summary**button.  The**Show agile board** button brings up the Agile board, which is now dedicated to the current sprint.  Placing an item on the last column of the agile board now means that the item is ‘done’.  The blue line on the Burndown chart then goes down by the number of points of that particular item.  That same item on the current sprint backlog, which is visible when clicking on the **Show backlog** button, now shows a ✓.

The **Finish selected sprint**button (**✓**) ends the current sprint.  Items that were not yet completed are moved to the next sprint’s backlog and remain on the agile board.  This brings the user to the next sprint planning, where items can easily be dragged from the product backlog to the next sprint backlog.  Note that in the top right of the sprint backlog the total number of points for that sprint is automatically calculated.

To start the next sprint, just click the **Start selected sprint** button, which is now available in the header menu.  The newly selected items are then taken off the product backlog and placed on the first column of the related Agile board.  The unfinished items are also still on the Agile board, in the columns where they were when the previous sprint was ended.

Adding Scrum to the already existing capabilities of Xurrent means that Scrum teams can now work fully in Xurrent, without the need for another tool to manage the various Scrum events and artifacts.
