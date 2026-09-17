# Engineering/Recipes.md

Short, reusable, copy-ready implementations for common Xurrent engineering needs. Each entry is self-contained. Append new recipes below following the same structure — do not create a separate file per recipe.

---

## Recipe: Injecting Phases and Tasks from a Workflow Template into an Already-Running Workflow (via REST API)

### When to use it

A Workflow is already running and needs to be extended or reshaped with the Phases/Tasks of a *different* Workflow Template than the one it was created from — without recreating the Workflow. There is no native shortcut for this (see `Engineering/KnownLimitations.md`); this sequence replicates, via the REST API, what the Gantt's "Apply Workflow Template..." action does internally.

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

- `Engineering/KnownLimitations.md` — "No REST endpoint exposes a Workflow Template's Task predecessor/successor sequence", "No bulk "apply Workflow Template" REST endpoint exists", "Workflow.template is historical only — updating it does not transform the Workflow"
- `Engineering/Debugging.md` — API/Postman troubleshooting notes relevant to building and testing this sequence
- `Platform/AutomationRules.md` — if triggering this sequence from an Automation Rule via `Call`/`Payload` to a Webhook

---

## Recipe: Detecting a Phase Change on Completion Target (Automation Rule pattern)

### When to use it

An Automation Rule needs to react specifically to a Workflow's Phase changing — e.g. to run phase-entry logic — by inspecting which Task is currently `assigned` and reading its Phase, rather than comparing the Workflow's own phase field directly.

### Pattern

```
Trigger: On update of Completion Target
  (evaluates whether the Workflow's phase has changed)

Expression 1 — first_assigned_task
  tasks.select(status = assigned)[first]

Expression 2 — current_phase_name
  expression1.phase_name

Condition
  expression2 = "Implementation Phase"
```

### Notes

- [Hypothesis] The exact official name of the trigger ("On update of Completion Target") and the comparison operator used in the Condition step are reconstructed from a shorthand note — verify the trigger's precise official name before relying on this in production. The Condition is written here using the confirmed `=` comparison operator.
- `tasks.select(status = assigned)[first]` follows the confirmed `collection.select(condition)` operator pattern — see `Platform/AutomationRules.md` — "Expressions — Confirmed Operators".

### Related entries

- `Platform/AutomationRules.md` — "Expressions — Confirmed Operators", "Ternary Evaluation Order"

---

## Recipe: Safe hide-and-clear pattern for conditional UI Extension fields

```js
function toggleConditionalField(parentField, childField) {
  var isVisible = (parentField.val() === 'yes');
  var row = childField.closest('.uix-row');

  if (isVisible) {
    row.show();
  } else {
    row.hide();
    // Guard: only clear+trigger if there's an actual value to clear.
    // Omitting this causes infinite recursion when childField is also
    // part of the shared change-handler's driver list.
    // See Engineering/Debugging.md → "Maximum call stack size exceeded".
    if (childField.val() !== '') {
      childField.val('').trigger('change');
    }
  }
}
```

Use `.show()`/`.hide()`, never `toggleClass()`, under the `uix-row` (Q1 2026+) layout — see `Engineering/KnownLimitations.md`.

### Related entries

- `Engineering/Debugging.md` — "Maximum call stack size exceeded" from a UI Extension change handler
- `Engineering/KnownLimitations.md` — "Dynamic `required` toggling on custom UI Extension fields has no effect", "`.toggleClass()` on `.uix-row` is unreliable under the Q1 2026 layout"

---

## Recipe: Migrating a legacy UI Extension (`row`) to the modern layout (`uix-row`)

### Source

Official Xurrent product update, January 29, 2026 — "Improved Record Layout for Better Readability".

### What changed

Xurrent introduced a new default form layout (labels placed above fields, left-aligned, consistent spacing). UI Extensions created before this update keep the old look unless migrated manually; UI Extensions built with the UI Extension Designer adopt it automatically.

### Migration steps

1. Rename every wrapping class from `row` to `uix-row` in the extension's HTML (e.g. `class="row vertical"` → `class="uix-row"`). This is the only change officially documented as required.
2. If any label is long enough to wrap onto multiple lines, add a CSS override — the new layout's default label style truncates long text with an ellipsis instead of wrapping:
   ```css
   .uix-row label {
     white-space: normal;
     overflow: visible;
     text-overflow: clip;
     word-break: break-word;
   }
   ```
3. Any JavaScript that shows/hides rows must use jQuery's `.show()`/`.hide()` — see `Engineering/KnownLimitations.md` — "`.toggleClass()` on `.uix-row` is unreliable under the Q1 2026 layout".
4. Wrap each date/time field's input in a `.row-value` div nested inside the `.uix-row`, matching the standard row structure — otherwise the date and time controls wrap onto separate lines instead of sitting on the same horizontal line:
   ```html
   <div class="uix-row">
     <label for="emrg_ctc_date_time" title="Emergency Contact - Date/Time">Emergency Contact - Date/Time</label>
     <div class="row-value">
       <input id="emrg_ctc_date_time" type="text" autocomplete="off" class="date-time">
     </div>
   </div>
   ```
5. Before activating, insert a native Snippet from the UI Extension editor (which already reflects the new layout) and compare its generated markup against the migrated extension, to catch any modifier class (e.g. `checkbox`) the official note didn't mention explicitly.

### Status

[Confirmed] for steps 1–4 (verified in this project's own UI Extensions).

### Notes

Cross-reference `Engineering/KnownLimitations.md` entries on `required` toggling and `.toggleClass()` visibility — both were discovered while migrating an extension under this same layout change.
