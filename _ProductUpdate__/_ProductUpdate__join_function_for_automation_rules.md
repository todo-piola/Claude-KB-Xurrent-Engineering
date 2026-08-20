---
title: "Join Function for Automation Rules"
date: "July 19, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/join-function-for-automation-rules"
slug: "join-function-for-automation-rules"
---

# Join Function for Automation Rules

A new function has been added to the automation rules to provide[more flexibility when working with strings](https://www.xurrent.com/product-updates/string-manipulation-operators-for-automation-rules).  The Join function creates and returns a new string by concatenating the elements in an array, separated by commas or a specified separator string.

One example of usage for this new function is the possibility to write comma-separated array elements to a note as a list, where all elements are written on a new line.  Even though in principle this was already possible by replacing the separator by a newline, this method would fail whenever the separator (a comma, for example) was used within the original array.

In the following screenshots, an automation rule that produces output with three methods: ‘cis’, ‘replaced’ and ‘joined’ is shown.  ‘Cis’ shows the array as a string with the original separators.  ‘Replaced’ replaces the separators by newlines, and ‘joined’, using the new function, joins every array element with a newline.

This automation rule produces the following output in the Staging environment:

