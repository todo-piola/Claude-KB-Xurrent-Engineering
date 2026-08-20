---
title: "Prevent Links with Change Template That Have No Justification"
date: "October 18, 2019"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/prevent-links-with-change-template-that-have-no-justification"
slug: "prevent-links-with-change-template-that-have-no-justification"
---

# Prevent Links with Change Template That Have No Justification

When a request template is placed in Edit mode, it used to be possible to link it to a change template which Justification field is empty. This would lead to a situation where the request template could be applied to a request, but the request could not be saved because a change cannot be generated without a value in its Justification field.

To prevent this situation going forward, it is no longer possible to save a request template if it is linked to a change template in which a justification has not been selected. The validation error message: “The Justification field of the Change Template can’t be blank” gets displayed when someone tries to do this.

In addition, the Justification field of a change template can no longer be emptied when this change template is linked to one or more request templates.
