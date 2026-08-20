# _Engineering__Recipes.md

Short, reusable, copy-ready implementations for common Xurrent engineering needs. Each entry is self-contained. Append new recipes below following the same structure — do not create a separate file per recipe.

---

## Recipe: Injecting Phases and Tasks from a Workflow Template into an Already-Running Workflow (via REST API)

### When to use it

A Workflow is already running and needs to be extended or reshaped with the Phases/Tasks of a *different* Workflow Template than the one it was created from — without recreating the Workflow. There is no native shortcut for this (see `_Engineering__Known_Limitations.md`); this sequence replicates, via the REST API, what the Gantt's "Apply Workflow Template..." action does internally.

### Call sequence

No `successor_ids` are needed anywhere — each Task declares its own `predecessor_ids` at creation time, and creation always proceeds in topological order (predecessors before successors), so the full dependency graph can be built using only `predecessor_ids`.

```
STEP 1 — Read the source Workflow Template's Phases
  GET /workflow_templates/:template_id/phases
  → returns [{ id, name, position }, ...]
  Note: these `id` values belong to the TEMPLATE. They cannot be reused
  on the target Workflow — new Phase records must be created there,
  yielding new ids.

STEP 2 — Create each Phase on the target Workflow (one call per phase)
  POST /workflows/:workflow_id/phases
  Body: { "name": "<phase name>", "position": <n> }
  → capture the returned `id` and build a map { phase_name → new_phase_id }

STEP 3 — Read the source Workflow Template's Task Template relations
  GET /workflow_templates/:template_id/task_template_relations
  → returns [{ id, phase_name, task_template: { id, subject } }, ...]
  Gives WHICH tasks belong to the template and WHICH phase each belongs
  to. Does NOT give execution order — see the "predecessor/successor
  sequence" entry in _Engineering__Known_Limitations.md.

STEP 4 — Create each Task on the target Workflow, in topological order
  POST /workflows/:workflow_id/tasks
  Body: {
    "template_id": <task_template id>,
    "phase_id": <mapped phase id from Step 2, or omitted if phase is null>,
    "predecessor_ids": [<ids of already-created predecessor tasks>]
  }
  → capture the returned `id` for use as a predecessor of later tasks.

STEP 5 (optional, cosmetic only) — Update the Workflow's template pointer
  PATCH /workflows/:workflow_id
  Body: { "template_id": <source template id> }
  Purely for audit/reporting labeling. Has NO functional effect — see
  _Engineering__Known_Limitations.md, "Workflow.template is historical
  only".
```

### Confirmed field names (live-tested, `201 Created`)

```json
POST /workflows/:workflow_id/tasks
{
  "template_id": <task_template_id>,
  "phase_id": "<phase_id>"
}
```

The response confirmed the Task was correctly linked to its `template` and `phase`. Same pattern confirmed for `predecessor_ids` as an array of integers on a subsequent call.

### Deriving the predecessor/successor order for Step 4

Since no REST endpoint exposes this graph, export the source Workflow Template (CSV/XLSX) and parse its `Workflow` column, which uses this notation:

```
'Task A' => 'Task B'
'Task C','Task D','Task E' => 'Task F'      (multiple predecessors joining one successor)
```

Validated to correctly represent both simple chains and many-to-one joins (multiple parallel predecessor Tasks converging into a single successor Task). Treat the resulting graph as static configuration per source template — do not re-derive it live on every execution.

### Related entries

- `_Engineering__Known_Limitations.md` — "No REST endpoint for Workflow Template task sequence", "No bulk apply-template endpoint", "Workflow.template is historical only"
- `_Engineering__Debugging.md` — API/Postman troubleshooting notes relevant to building and testing this sequence
- `_Platform__Automation_Rules.md` — if triggering this sequence from an Automation Rule via `Call`/`Payload` to a Webhook
