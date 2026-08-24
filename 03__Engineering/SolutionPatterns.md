# Engineering/SolutionPatterns.md

Solution design patterns for recurring Xurrent workflow-governance and digital/business-process scenarios. Append new patterns below — do not create a separate file per pattern.

---

## Pattern Family: Routing a Workflow to Different Follow-Up Tasks Based on a Chosen Value

**Applies to:** Change Management / Digital business processes / any scenario where a Workflow's subsequent Tasks depend on a category, subtype, or classification value chosen by a participant.

Three fundamentally different patterns exist. Which one applies depends on **where and when** the routing decision is made relative to the Workflow's lifecycle.

### Pattern 1 — Native, zero-code: per-category Request Template chain

**Mechanism:** instead of one generic Request Template with a form field, create one Request Template per category, each with `status = workflow_pending` and its own `workflow_template`. The requester picks the category by picking the Request Template. Xurrent auto-generates the correct Workflow — no custom code, no Automation Rule, no Webhook.

**Confirmed native mechanism it relies on:**
- `Task Template.request_template` — used to generate a new Request when a Task based on the Task Template is started (Assigned/Accepted/In Progress).
- `Request Template.status` + `Request Template.workflow_template` — when the generated Request reaches `workflow_pending` with a `workflow_template` set, Xurrent auto-generates the Workflow, with normal (non-halted) task assignment.

**Only viable when the routing decision is made at (or before) Workflow creation.** Not viable once the Workflow is already running and the decision happens mid-flow — see Patterns 2 and 3.

### Pattern 2 — "Inject" (build only what's needed)

The Workflow starts minimal. When the routing decision is made mid-flow, an external service creates — via the REST call sequence in `Engineering/Recipes.md` — only the Phases/Tasks belonging to the chosen path.

### Pattern 3 — "Superset + cancel"

A single Workflow Template contains **all** possible Tasks upfront, for every path. When the routing decision is made, an Automation Rule cancels the Tasks belonging to the path(s) **not** chosen:

```
Expressions:
tasks_to_cancel: workflow.tasks.reject(<condition matching the chosen path>)

Actions:
a1: update tasks_to_cancel set status = canceled
```

Natively achievable with a single Automation Rule action — see `Platform/AutomationRules.md`, "Updates", for the confirmed collection-level `Update` behaviour this relies on.

**Confirmed viability condition:** cancelling a predecessor Task releases its successor to advance — see `Engineering/KnownLimitations.md`. This means Pattern 3 does not leave the chosen branch permanently blocked, as long as the graph is designed so the chosen branch's own predecessors are never among the cancelled set.

### Comparison

| Criterion | Pattern 2 — Inject | Pattern 3 — Superset + Cancel |
|---|---|---|
| Automation Rule complexity | High — requires an external webhook/service; a native Automation Rule alone cannot loop or create Phases (see `Engineering/KnownLimitations.md`). | Low — a single native `Update` action with `select()`/`reject()`; potentially zero external code for the cancellation step itself. |
| Gantt/template hygiene | Each path lives in its own, focused Workflow Template — clean, but that template is only ever consumed via API, never literally "applied" in the UI. | One dense Gantt mixing every path's Tasks and cross-branch predecessor/successor wiring. Gets harder to read as paths are added. |
| Scaling to a new path | Add a new Workflow Template + one more routing branch. Each path's Gantt stays isolated. | Add more Tasks to the superset template and adjust the cancellation condition. The single Gantt keeps growing indefinitely. |
| Team/queue noise | Tasks belonging to non-chosen paths never exist in the real Workflow. | All paths' Tasks are instantiated momentarily, then cancelled — can transiently appear in other teams' queues and pollute "tasks per team" metrics. |
| Differing Phases per path | No problem — each path defines its own Phases. | Forces a Phase structure shared across all paths even if they don't conceptually share stages. |

Neither pattern is universally better. As a rule of thumb: paths that share most Tasks and differ only in a few optional ones fit Pattern 3 more comfortably; paths that are substantially distinct domains fit Pattern 2 more comfortably. The two can also be combined — a shared base plus an injected divergent subset.

### Related entries

- `Engineering/Recipes.md` — the REST call sequence Pattern 2 depends on.
- `Platform/AutomationRules.md` — the collection-`Update` mechanism Pattern 3 depends on.
- `Engineering/KnownLimitations.md` — constraints that rule out a native, code-free version of Pattern 2.
