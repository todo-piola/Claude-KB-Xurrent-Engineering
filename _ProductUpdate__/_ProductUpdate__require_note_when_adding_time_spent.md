---
title: "Require Note when Adding Time Spent"
date: "February 13, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/require-note-when-adding-time-spent"
slug: "require-note-when-adding-time-spent"
---

# Require Note when Adding Time Spent

The Time spent field of a request, problem, change task or project task now becomes required whenever text has been entered in the Note field.  Some organizations, however, require a note that justifies the effort for every time entry that is created.  Such organizations are typically managed service providers (MSPs) and shared service centers of larger enterprises.  They are now able to activate the new timesheet settings option ‘Require note’.

When this option is checked in the timesheet settings of an organization, its people will notice that the Note field becomes required whenever they specify a value in the Time spent field.

Because a public note, as well as an [internal note](https://www.xurrent.com/product-updates/internal-notes), can be added to a request, some extra logic has been added. When the ‘Require note’ option is active and a specialist has entered a value in the Time spent field, this logic ensures that the public Note field becomes required.  But if the specialist enters some text in the Internal note field, the public Note field becomes optional again.  This way, the specialist is only required to add one note.

It may also be good to point out that, when a zero is entered in the Time spent field, a new time entry will not be generated when the record is saved.  Therefore, the Note field does not become mandatory when the Time spent field contains a 0 or 0:00.

