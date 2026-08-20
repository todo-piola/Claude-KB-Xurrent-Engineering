---
title: "Introducing Data Integrity Reports"
date: "August 23, 2023"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-data-integrity-reports"
slug: "introducing-data-integrity-reports"
---

# Introducing Data Integrity Reports

A new section has been added to the Xurrent Settings console of the Specialist Interface: Data Integrity Reports. Here, users can check whether there are any records that are referring to other records that are no longer enabled or available. This can be useful, for example, when a person has left the organization, but not all tasks have been reassigned to others. These reports are currently divided into reports on persons, products, organizations and services. It is expected that this section will be further expanded in the future.

Which reports are visible depends on the role of the person who is logged in:

- Service Desk Managers: reports on requests and request templates
- Problem Managers: problems
- Release Managers: releases
- Workflow Managers: workflows, workflow templates, tasks, and task templates
- Project Managers: projects, project tasks, and project task templates
- Service Level Managers: services, SLAs, FLSAs, and service instances
- Configuration Managers: configuration items, products, and shop articles
- Account Administrators and Auditors can see all data integrity reports

After clicking on any of these reports, the respective view is opened with all active or enabled records that are related to a disabled or unavailable record. In the example below, the ‘Problems With Disabled Member’ data integrity report shows the only problem record that is assigned to a disabled person record, in this case that of Grace Weller. This then enables the problem manager to easily update the member.

Currently, the following reports are available:

**Person Integrity Reports**• Requests With Disabled Member
• Request Templates With Disabled Member
• Problems With Disabled Member
• Releases With Disabled Manager
• Workflows With Disabled Manager
• Workflow Templates With Disabled Workflow Manager
• Tasks With Disabled Manager
• Tasks With Disabled Assignee
• Task Templates With Disabled Assignee
• Projects With Disabled Manager
• Project Tasks With Disabled Manager
• Project Tasks With Disabled Assignee
• Project Task Templates With Disabled Assignee
• Services With Disabled Responsible
• Service Level Agreements With Disabled Person
• First Line Support Agreements With Disabled Person
• Configuration Items With Disabled User
• Organizations With Disabled Manager
• Organizations With Disabled Substitute
• Teams With Disabled Manager
• Teams With Disabled Member
• Skill Pools With Disabled Manager
• Skill Pools With Disabled Member
• People With Disabled Manager
• Risks With Disabled Manager

**Product Integrity Reports**• Configuration Items With Disabled Product
Organization Integrity Reports
• Service Level Agreements With Disabled Customer Organization
• Service Level Agreements With Disabled Covered Organization
• Products With Disabled Organization

**Service Integrity Reports**• Service Level Agreements With Inactive Service Instance
• Service Level Agreements With Unavailable Service Offering
• Shop Articles With Unavailable Service Offering
