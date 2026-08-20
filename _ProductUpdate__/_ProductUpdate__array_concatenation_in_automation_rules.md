---
title: "Array Concatenation in Automation Rules"
date: "March 4, 2022"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/array-concatenation-in-automation-rules"
slug: "array-concatenation-in-automation-rules"
---

# Array Concatenation in Automation Rules

It is now possible to concatenate arrays in automation rules.  In the example that was given in a previous blog post about [attachments in UI extensions and automation rules](https://www.xurrent.com/product-updates/attachments-in-ui-extensions-and-automation), two arrays of attachments were combined in one note.  To combine the attachments of the first and last note of a workflow, for example, the following expressions can be used:

`notes: workflow.notes`

`e1: notes[last].attachments + notes[first].attachments`

The constraints for this + operator are as follows:

- The first operand must be an array
- The second operand must be either:an array of the same type as the elements of the first operand (i.e. one cannot concatenate ‘apples’ and ‘oranges’)a single item of the same type as the elements of the first operand
- Multiple concatenations may be performed in a single expression

More examples of what is allowed:

`notes: workflow.notes`

`e1: notes + notes[first] + notes[last] + notes`

`e2: workflow.requests[first].notes + notes + notes[first]`

`e3: find_all(people, 'beatrice.baldwin@widget.com') + workflow.manager`

Note that if the first operand is not an array, the result follows the normal (existing) rules for the + operator.  For example:

`e1: notes[first] + notes`

This is allowed, but the result is not an array of notes.  Instead, the notes are converted to strings and joined together using , (a comma).
