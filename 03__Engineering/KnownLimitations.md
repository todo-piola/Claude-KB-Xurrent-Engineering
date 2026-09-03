# Engineering/KnownLimitations.md

Verified or observed platform limitations and behaviours. Each entry follows the fixed structure defined in `00__ProjectInstructions/KnowledgeIndex.md`. Append new entries below — do not create a separate file per limitation.

---

## No API or Automation Rule equivalent for the Gantt "Apply Workflow Template..." action

### Problem
Whether the Gantt's "Apply Workflow Template..." action (which adds a chosen Workflow Template's Phases and Tasks onto an already-existing Workflow) has a documented REST, GraphQL, or Automation Rule equivalent.

### Expected behaviour
A bulk endpoint or Automation Rule action that replicates the button's effect in one call.

### Actual behaviour
No such endpoint or action exists. The button's own audit trail confirms it only creates Phase and Task records — nothing else (no other field changes).

### Verification
Reviewed the full Workflows / Workflow Templates API reference; cross-checked the button's effect against the Workflow's audit trail in a live sandbox.

### Status
[Confirmed]

### Workaround
See `Engineering/Recipes.md` — "Injecting Phases and Tasks from a Workflow Template into an Already-Running Workflow (via REST API)".

### Notes
—

---

## Workflow.template is historical only — updating it does not transform the Workflow

### Problem
Whether changing a Workflow's `template` field (via `PATCH /workflows/:id`) re-triggers creation of the corresponding Phases/Tasks.

### Expected behaviour
Unclear from the field's documentation alone — it could plausibly re-apply the template.

### Actual behaviour
No. `PATCH`ing `template_id` on an existing Workflow succeeds, but creates or alters no Phase or Task. The field's official definition — *"the workflow template that was used to register the workflow"* — is past-tense/registration-time only, consistent with this result.

### Verification
Live-tested: issued `PATCH /workflows/:id { "template_id": ... }` against a Workflow with a known set of Tasks/Phases, then confirmed via `GET` that no new records appeared and no existing ones changed.

### Status
[Confirmed]

### Workaround
None needed to know — this is a fact to design around, not a gap to patch. Use the Recipe above to actually transform the Workflow's content; use the `template` field update only for cosmetic/audit labeling, and only after the real transformation succeeds.

### Notes
—

---

## Automation Rules cannot create Workflow or Phase records

### Problem
Whether an Automation Rule action can create a new Workflow or a new Phase record.

### Expected behaviour
Unknown prior to checking — Automation Rules do support creating Task records via `new(task, ...)`, so a similar primitive for Workflow/Phase seemed plausible.

### Actual behaviour
No. The only documented creation primitive is `new(task, ...)`, explicitly scoped to Task records ("New records (only for tasks)").

### Verification
`help.xurrent.com/help/automation_rule_operators` (official documentation).

### Status
[Confirmed]

### Workaround
Phases and Workflows must be created via the REST API (or native platform flows), not via Automation Rule actions. See `Engineering/Recipes.md`.

### Notes
—

---

## Automation Rule expression language has no loop/iteration construct

### Problem
Whether an Automation Rule expression can iterate dynamically over "all Task Templates belonging to Workflow Template X" to create matching Tasks in one expression.

### Expected behaviour
Some form of `each`/`for`/map-with-side-effects construct.

### Actual behaviour
No such construct exists. Every `new(task, 'Subject')` call must be written explicitly, one per Task Template — there is no way to loop over an arbitrary template's structure at rule-evaluation time.

### Verification
Reviewed official Automation Rule operators documentation; no iteration operator is documented (only `select`/`reject`/`map`-style operations over already-existing collections, not over template definitions to spawn new records).

### Status
[Confirmed by absence]

### Workaround
Hardcode the set of `new(task, 'Subject')` calls per known Workflow Template/family as static rule content, or move the logic to an external service driven by a Webhook (see `Integrations/Webhooks.md`) if the set of templates is large or changes often.

### Notes
—

---

## No bulk "apply Workflow Template" REST endpoint exists

### Problem
Whether the REST API exposes an endpoint to apply an entire Workflow Template (all its Phases and Tasks) onto an existing Workflow in a single call.

### Expected behaviour
A single `POST` accepting a `template_id` and doing the equivalent of the Gantt action.

### Actual behaviour
No such endpoint exists. The only way is issuing one `POST` per Phase and one `POST` per Task.

### Verification
Full review of the Workflows and Workflow Templates API reference documentation.

### Status
[Confirmed]

### Workaround
See `Engineering/Recipes.md`.

### Notes
—

---

## No REST endpoint exposes a Workflow Template's Task predecessor/successor sequence

### Problem
Whether any REST endpoint documents the execution order (predecessor → successor) between the Task Templates of a Workflow Template.

### Expected behaviour
A field or nested endpoint alongside `task_template_relations` describing dependency order.

### Actual behaviour
`GET /workflow_templates/:id/task_template_relations` gives Task Template membership and Phase assignment, but not execution order. No REST endpoint exposes the dependency graph directly. It is only exposed via the Workflow Template's CSV/XLSX export, in a `Workflow` column using `'A' => 'B'` notation (including many-to-one joins: `'A','B','C' => 'D'`).

### Verification
Reviewed `task_template_relations` API response fields; cross-checked against a real Workflow Template's CSV/XLSX export, confirming the `Workflow` column correctly encodes both simple chains and multi-predecessor joins.

### Status
[Confirmed]

### Workaround
Export the source Workflow Template once per family/template and parse the `Workflow` column to derive the topological order; store it as static configuration rather than re-deriving it live on every execution.

### Notes
—

---

## Cancelling a predecessor Task releases its successor

### Problem
Whether cancelling a Task that is a predecessor of another Task unblocks that successor Task to advance (e.g. to `assigned`), or leaves it permanently stuck waiting on a predecessor that will never complete.

### Expected behaviour
Undocumented — could go either way depending on whether the platform treats "cancelled" as equivalent to "resolved" for dependency-release purposes.

### Actual behaviour
Cancelling a predecessor Task does release its successor to advance.

### Verification
Live-tested in a sandbox Workflow with two Tasks in a predecessor → successor relationship: cancelled the predecessor, observed the successor transition to `assigned` on its own.

### Status
[Observed]

### Workaround
Not applicable — this is a positive finding, not a limitation. It enables designs where discarded branches are cancelled without permanently blocking the chosen branch, as long as the chosen branch's own predecessors are never among the cancelled set.

### Notes
—

---

## Task/Phase creation endpoints reject batched arrays

### Problem
Whether `POST /workflows/:id/tasks` or `POST /workflows/:id/phases` accept an array of objects to create multiple records in a single call.

### Expected behaviour
Uncertain — some REST APIs support batch creation via arrays.

### Actual behaviour
No. Sending a JSON array as the body returns `{"message": "Invalid JSON string posted"}`. Exactly one JSON object per call is required.

### Verification
Live-tested: posting an array of 4 Phase objects in one call to `POST /workflows/:id/phases` returned the error above; posting one object per call succeeded.

### Status
[Observed]

### Workaround
Issue one `POST` per record, sequentially.

### Notes
—

---

## API host for legacy-branded ("4me.qa") domain accounts may differ from the documented Service URL table

### Problem
Which API host (`baseUrl`) is correct for an account whose UI still runs on the legacy "4me" branded domain (e.g. `*.4me.qa`) rather than the current `xurrent.*` naming.

### Expected behaviour
The officially documented Service URL table only lists `api.xurrent.com` / `api.xurrent.qa` / `api.xurrent-demo.com` — no `4me.qa` variant is documented.

### Actual behaviour
For the tested account, `https://api.4me.qa/v1` was the working API host (confirmed via a successful authenticated call), not the documented `api.xurrent.qa`.

### Verification
Live-tested: calls against `https://api.xurrent.qa/v1` were not confirmed to work for this account; calls against `https://api.4me.qa/v1` succeeded (`200 OK` on `/me` and subsequent endpoints) once authentication was correctly configured.

### Status
[Observed — account/environment specific]

### Workaround
Do not assume the documented Service URL table applies to every account, particularly older or legacy-branded ones. Verify the working API host empirically (e.g. a `GET /me` sanity check) before building an integration against a new account.

### Notes
Observed on a `*.4me.qa` account (pre-rebrand domain naming). May not apply to accounts already fully migrated to `xurrent.*` domains.

---

## Automation Rules that force-complete a Request after an approval rejection bypass Progress Halted and inherit the account owner for team/member re-assignment

### Problem
What happens to a Workflow/Request when an approval Task is rejected — natively, versus when a custom Automation Rule intervenes to complete the Workflow/Request immediately after the rejection instead of leaving it halted?

### Expected behaviour
Native Xurrent behaviour: when an approver rejects an approval Task, the Workflow moves to `Progress Halted`, the Workflow Manager is notified, and the Request is left completely untouched — not automatically completed, not reassigned. The intended design is for a real person (the owning team) to review and close the Request themselves after a rejection.

### Actual behaviour
When a custom Automation Rule instead sets the Workflow/Request status to `Completed` immediately after the rejection (bypassing `Progress Halted`), Xurrent's mandatory team/member resolution for `Completed` uses the **account owner** as the acting identity — because Automation Rules execute as the account owner (see `Platform/AutomationRules.md`). Neither the Workflow Manager, nor whoever completed the last Task, nor whoever triggered the rule is used. If the account owner does not belong to the Request's current team, Xurrent silently moves the Request to a team the account owner belongs to and sets the account owner as `member`, even though the account owner had no real involvement in the case. This can misdirect closed Requests to unrelated teams and pollute team/ownership reporting.

### Verification
Confirmed by Xurrent Support, including a live reproduction of the native rejection flow in a clean Xurrent environment (isolated from customer-specific Automation Rules), cross-referenced against the official KA *"What are the rules for request re-assignment on Completion or Waiting for Customer."*

### Status
[Confirmed]

### Workaround
- Prefer letting a rejected Workflow remain in `Progress Halted` (the native flow) instead of using a custom Automation Rule to force it to `Completed` — this keeps a real, relevant person on record as the one who closes the Request.
- If a Request/Workflow *must* be auto-completed by an Automation Rule, set `team` and `member` **explicitly** in the same action, instead of relying on Xurrent's default derivation.
- Do not "fix" the side effect by adding the account owner to more operational teams — that spreads the same effect to every team they belong to, instead of removing it.
- Test any such rule outside production first.

### Notes
See `Platform/AutomationRules.md` — "Request/Workflow Completion — Team & Member Assignment" — for the general (non-Automation-Rule) version of the resolution rule this entry depends on.

---

## Task Not Appearing in Change Calendar Despite Category = Implementation

**Problem** — A Task has `category = Implementation` and belongs to a Change (Workflow), but does not show up in the Change Calendar even without any filters applied.

**Expected behaviour** — Any Task with `category = Implementation` belonging to a Change should be visible in the Change Calendar.

**Actual behaviour** — The Task is silently omitted from the Change Calendar view.

**Root cause** — The Task is not `linked` to a Service Instance. The Change Calendar requires a Service Instance link in addition to `category = Implementation`; this is not enforced or flagged anywhere in the UI at Task creation time.

**Verification** — Confirmed against official Xurrent Product Update documentation (see `Platform/ReportingAnalytics.md` → "Change Calendar — Visibility Requirements" for sources).

**Status** — [Confirmed]

**Workaround** — Link the relevant Service Instance to the Task (or ensure the Task Template used generates the link automatically) before expecting it to appear on the Change Calendar.

**Notes** — See `Platform/ReportingAnalytics.md` for the full set of Change Calendar visibility requirements (category, Workflow membership, Service Instance link) and additional filter/rendering behaviour.
