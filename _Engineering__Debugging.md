# _Engineering__Debugging.md

Debugging techniques, common errors, and troubleshooting methodology. Append new entries under the relevant subsection below — do not create a separate file per finding.

---

## Automation Rule Debugging

### Actions within a rule execute as a single transaction

If one action in an Automation Rule fails (e.g. a `new(task, ...)` whose resulting successor link is rejected), the entire batch of actions in that run is aborted — including actions that, in isolation, would have succeeded. A later, unrelated-looking error (e.g. a generic `"Unknown error"` on a subsequent action) is very likely a **cascade failure** from an earlier action in the same run, not an independent bug.

**Methodology:** when a rule with multiple actions fails, do not immediately assume multiple bugs. Isolate and test the smallest failing expression/action alone in the Rule Execution Viewer first; only investigate further actions once the first genuine failure is fixed.

### `new(task, 'Subject')` requires the Task Template to belong to the target's Workflow Template

If a Task Template referenced by `new(task, 'Subject')` is not linked to the Workflow Template that the current Workflow was created from, the resulting attempt to wire it as a successor fails with:

```
Successors must be linked to the same workflow
```

Fix: link the Task Template to the Workflow Template first (`POST /workflow_templates/:id/task_templates?task_template_id=...`), then re-run the rule.

---

## API / Postman Debugging

### A generic 401 with `{"message": "Unauthorized"}` usually means a malformed or missing Authorization header

More often than an actually-invalid token, a `401` with this exact body reflects the `Authorization` header not being sent correctly at all (empty, missing the `Bearer ` prefix, or containing an unresolved template variable). Before assuming the credential itself is bad, inspect the literal outgoing request (via a request-inspection console, or a generated code snippet) to confirm what was actually sent.

### Postman-specific gotchas

- Variables of type `secret` are redacted in generated code snippets and in "Variables in request" panels — this can look like the variable is empty even when it resolves correctly at send time. Temporarily switching the type to `default` is the fastest way to confirm the real value is present.
- The "Inherit auth from parent" option only appears on a request once it is saved **inside** a Collection — a request created standalone has no parent to inherit from.
- A stray leading/trailing space pasted into a variable (e.g. a numeric ID) silently breaks the resulting URL and typically surfaces as a `404 Not Found` rather than an obviously-malformed-request error. Worth checking first whenever a 404 appears on an endpoint that should exist.

### `404 Not Found` can indicate a permissions issue, not a missing record

Xurrent may return `404` (rather than `403`) when a record exists but is not accessible with the current credentials/scopes — a common practice to avoid revealing record existence to unauthorized callers. When a `404` appears on an endpoint/ID that should be valid, check the credential's scopes before assuming the ID is wrong.

### Bisection for unexpected errors on nested/sub-resource endpoints

When a call to a sub-resource (e.g. `/workflow_templates/:id/phases`) fails unexpectedly, first test the parent resource alone (`/workflow_templates/:id`) to determine whether the failure is about access to the parent record itself, or specific to the sub-resource endpoint.

---

## Common Data-Entry Errors

- Batch/array bodies are rejected by creation endpoints that expect a single object — see `_Engineering__Known_Limitations.md`, "Task/Phase creation endpoints reject batched arrays".
