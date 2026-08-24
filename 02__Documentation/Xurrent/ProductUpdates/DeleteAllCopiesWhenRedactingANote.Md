---
title: "Delete All Copies When Redacting a Note"
date: "March 21, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/delete-all-copies-when-redacting-a-note"
slug: "delete-all-copies-when-redacting-a-note"
---

# Delete All Copies When Redacting a Note

Account administrators have the ability to [remove notes](https://www.xurrent.com/product-updates/delete-notes).  This makes to possible for them to act when someone accidentally included sensitive information in a note, or attached a file that contains information that should not have been shared.

But sometimes notes are copied to other records.  For example, problem managers can cause a note that they are adding to a problem to be copied to all requests that are related to the problem.  Or a specialist may cause a note to be copied from a task to the change that the task is a part of.  And then there are the notes that are added to request groups.  Such notes are copied to all requests that belong to the group.

To ensure that not a single copy of a deleted note remains, Xurrent now automatically redacts all notes that are a copy of the note that an administrator has deleted, as well as the note that was the original of the note that was deleted, along with any other notes that are copies of that same original.
