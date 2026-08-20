---
title: "Introducing Skill Pools"
date: "November 18, 2019"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-skill-pools"
slug: "introducing-skill-pools"
---

# Introducing Skill Pools

Not too long ago it became possible to [assign project tasks to teams](https://www.xurrent.com/product-updates/assign-project-tasks-to-teams).  Now another project management feature has become available.  This one allows project managers to assign tasks to skill pools.  A skill pool is a group of people who share a specific capability.  Unlike teams, the members of a skill pool do not need to have the [Specialist role](https://help.xurrent.com/help/specialist_role/).  The new Skill Pool functionality adds a new resource-planning dimension.

Skill pools are primarily intended to be used by project managers when they are planning a project.  They can link a task to a skill pool if this task needs to be completed by someone who has the expertise of the skill pool.  By linking a skill pool, the project manager does not yet need to know the specific individual who will perform the work.

A message is displayed in the project task to inform the project manager that the task will eventually need to be assigned to a member of the skill pool if no assignees are selected yet.  This does not, however, prevent the project manager from starting the project.

The status of a project task will automatically be updated to ‘Assigned’ after its predecessors have been completed.  When this happens and the task is linked to a skill pool, but not yet for an individual skill pool member, the project manager receives a notification.  The task then also becomes visible in the project manager’s inbox.

This should prompt the project manager to find the right skill pool member to assign the task to.  The project manager may want to discuss this with the manager of the skill pool (provided that one has been assigned to it) or with the direct managers of the individual members of the skill pool.

A resource planning overview has also been added specifically for skill pools.  It can be opened from the Actions menu of the Inbox console, from the Actions menu after opening a skill pool in the Records console, or it can be found in the ‘Resource Planning’ section of the Analytics console.  This overview behaves the same as the one for teams.  It helps managers find a member of the skill pool who still has enough availability to get the task completed.

As long as a skill pool is linked to a project task, only the members of this pool can be selected as its assignees.  It is possible for the project manager to link both a team and a skill pool to a task.  That limits the people to whom the task can be assigned to those who are a member of the team as well as the skill pool.  This can be useful when the task may only be handled by a subsection of the team, e.g. application developers who know how to build mobile apps.

If Xurrent’s workflow automation updates the status of a project task to ‘Assigned’ and this task is assigned to a team and a skill pool, but not yet to a specific assignee, then the coordinator of the team is notified rather than the project manager.  The task will then also be visible in the team coordinator’s inbox so that the coordinator can forward the task to a specific member of the team who is also a member of the task’s skill pool.  If the team does not have a coordinator, then each team member, who is also a member of the skill pool, is notified and will see the task in his or her inbox.

#### Activating the Skill Pool Functionality

The Skill pool field becomes available in project tasks as soon as the first skill pool has been registered in the account of the task’s project.  Account administrators can register and maintain skill pools.  The person who is linked to a skill pool as its manager is also allowed to edit this specific skill pool, provided that the manager has the Specialist role to access Xurrent’s full UI.

Any person who is registered in the same account as a skill pool, or the skill pool’s directory account, can be related as the manager or a member of the skill pool.  Unlike the members of teams, these people do not need to have the Specialist role to become a member of the skill pool.  People from any other Xurrent account, who have the Specialist role of the account in which the skill pool is registered, can also become a member of the skill pool.
