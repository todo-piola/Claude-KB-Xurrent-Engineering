# Platform/AutomationRules.md

Automation Rule structure, operators, and confirmed platform behaviour. This file is populated incrementally — sections with no confirmed content yet are omitted rather than left as empty placeholders; add them as knowledge is verified.

---

## Expressions — Confirmed Operators

Source: `help.xurrent.com/help/automation_rule_operators` (official).

| Operator / pattern | Confirmed behaviour |
|---|---|
| `new(task, 'Task Template Subject')` | Creates a new Task in the **same** Workflow, based on the named Task Template. Only works for Task records — no `new(workflow, ...)` or `new(phase, ...)` exists. |
| `collection.select(condition)` / `collection.reject(condition)` | Filters a collection. Function-call syntax with parentheses — **not** Ruby block syntax (`{ }`). |
| `workflow.tasks['Subject']` | Indexes a Task within a Workflow by its (ideally unique) subject. |
| `condition then X else Y` | Ternary expression. |

## Updates

Confirmed: the `Update` field can target a **whole collection**, not just a single record (e.g. `workflow.requests`, or `workflow.tasks.select(...)`) — the corresponding `Set`/`Add`/`Remove` action then applies to every record in that collection in one action, without needing to loop.

## Execution Behaviour

- All actions within a single Automation Rule execution run as **one transaction**: if one action fails, the entire batch is aborted, including actions that would otherwise have succeeded. See `Engineering/Debugging.md` — "Actions within a rule execute as a single transaction" — for the resulting debugging implication.
- `new(task, 'Subject')` requires the referenced Task Template to already be linked to the Workflow Template that the current Workflow was created from; otherwise wiring it as a predecessor/successor of an existing Task fails with `"Successors must be linked to the same workflow"`.
- Automation Rules execute as the **account owner**. This matters whenever a Rule's action changes a field whose value or side effects depend on "who performed this" — e.g. completing a Request (see below). [Confirmed — Xurrent Support, live reproduction in a clean environment.]

## Request/Workflow Completion — Team & Member Assignment

Per official KA *"What are the rules for request re-assignment on Completion or Waiting for Customer"*: a Request cannot be set to `Completed` (or `Waiting for Customer`) without both `team` and `member` populated. Which identity Xurrent derives them from depends on **what performs the completion**.

### Native workflow-driven completion

When a Workflow completes its Request through the standard flow (not a custom Automation Rule forcing completion early), Xurrent does **not** use whoever completed the last Task. It uses the Workflow's **Manager**:

- `member` = the Workflow's Manager.
- `team` = the first team the Manager belongs to, resolved in this fixed order:
  1. The Service Desk team of the Request's account.
  2. The Service Desk team of the Service Instance's account.
  3. The Service Instance's First Line team.
  4. The Service Instance's Support team.
  5. The first enabled team the Manager belongs to, in either account.

Whoever is Manager when the Workflow **starts** is who the Request lands on after workflow completion.

To keep completion statistics/ownership clean, since assignment follows the Workflow Manager, do one of:
- Set the Workflow Template's Manager to whoever's first team should own the closure, or
- Enable *Assign after workflow completion* on the template and set a fixed team there, or
- Set `team` and `member` explicitly via a custom Automation Rule instead of relying on the default derivation.

[Confirmed]

### Forced completion (person or Automation Rule setting `status` directly)

When completion is instead forced directly — a person manually completing the Request, or a custom Automation Rule setting `status = completed` / `waiting_for_customer` outside the native workflow-driven flow — the Workflow Manager is **not** used. Xurrent derives `team`/`member` from the identity performing that action instead:
- If that identity already belongs to the Request's current team, it is simply set as `member`.
- If not, Xurrent **moves the Request to a team the identity belongs to** and sets that identity as `member`.

When the identity performing the completion is an **Automation Rule**, the identity used is the account owner — see `Engineering/KnownLimitations.md`, "Automation Rules that force-complete a Request after an approval rejection bypass Progress Halted and inherit the account owner for team/member re-assignment," for the practical consequence and workaround.

[Confirmed]

*Correction note:* this section previously stated that neither the Task-completer nor the Workflow Manager is ever part of the resolution logic. That statement only held for the forced-completion path above; it did not correctly describe native workflow-driven completion, which does use the Workflow Manager as detailed here. This is the corrected version.

### Workflow Manager — Request Template vs. Workflow Template precedence

When a Request Template has an associated Workflow Template, and both specify a Manager (the Request Template's own Manager field, and the Workflow Template's Manager field), the two can differ. The **Request Template's Manager takes precedence** — it is the one set as the Workflow's Manager once the Workflow is created from that Request.

[Confirmed]

## Ternary Evaluation Order

Expressions are written top-to-bottom, but nested/chained ternary (`condition then X else Y`) expressions are evaluated bottom-to-top. In a chain of ternaries, the rule keeps the result of whichever branch is evaluated last — the one written closest to the bottom / most deeply nested — as the highest-priority match. When designing a chain of ternaries meant to express a priority order, write the highest-priority condition last (closest to the bottom), not first.

[Observed]

## Known Automation Rule Constraints

- No creation primitive exists for Workflow or Phase records — only `new(task, ...)` for Tasks. See `Engineering/KnownLimitations.md`.
- No loop/iteration construct (`each`/`for`) exists in the expression language — every `new(task, 'Subject')` call must be written explicitly, one per Task Template; there is no way to dynamically enumerate "all Task Templates of Workflow Template X" from within a rule. See `Engineering/KnownLimitations.md`.
- `Call` (Automation Rule field): selects a registered Webhook to invoke as part of the rule's actions.
- `Payload` (Automation Rule field): defines the JSON body sent to that Webhook, built from expressions.

## Naming

Task Template subjects referenced via `new(task, 'Subject')` or `tasks['Subject']` should be unique and descriptive per family/domain (e.g. `"Infra - Provision network"`, not `"Provision"`) — ambiguous resolution is a real risk if subjects repeat across templates.

## Related entries

- `Engineering/Recipes.md` — practical use of `new(task, ...)`-adjacent patterns via the REST API when the expression language's constraints (no loop, no Phase/Workflow creation) make an in-rule solution insufficient.
- `_Engineering/KnownLimitations.md` — full detail and verification method for each constraint above.
