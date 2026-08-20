# _Platform__Automation_Rules.md

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

- All actions within a single Automation Rule execution run as **one transaction**: if one action fails, the entire batch is aborted, including actions that would otherwise have succeeded. See `_Engineering__Debugging.md` — "Actions within a rule execute as a single transaction" — for the resulting debugging implication.
- `new(task, 'Subject')` requires the referenced Task Template to already be linked to the Workflow Template that the current Workflow was created from; otherwise wiring it as a predecessor/successor of an existing Task fails with `"Successors must be linked to the same workflow"`.
- Automation Rules execute as the **account owner**. This matters whenever a Rule's action changes a field whose value or side effects depend on "who performed this" — e.g. completing a Request (see below). [Confirmed — Xurrent Support, live reproduction in a clean environment.]

## Request/Workflow Completion — Team & Member Assignment

Per official KA *"What are the rules for request re-assignment on Completion or Waiting for Customer"*: a Request cannot be set to `Completed` (or `Waiting for Customer`) without both `team` and `member` populated. Xurrent derives them from the identity that performs the completion action:
- If that identity already belongs to the Request's current team, it is simply set as `member`.
- If not, Xurrent **moves the Request to a team the identity belongs to** and sets that identity as `member`.

This applies regardless of who completed the last Task or who is the Workflow Manager — neither is part of the resolution logic, despite being intuitive candidates. When the identity performing the completion is an **Automation Rule**, the identity used is the account owner — see `_Engineering__Known_Limitations.md`, "Automation Rules that force-complete a Request after an approval rejection bypass Progress Halted and inherit the account owner for team/member re-assignment," for the practical consequence and workaround.

[Confirmed]

## Known Automation Rule Constraints

- No creation primitive exists for Workflow or Phase records — only `new(task, ...)` for Tasks. See `_Engineering__Known_Limitations.md`.
- No loop/iteration construct (`each`/`for`) exists in the expression language — every `new(task, 'Subject')` call must be written explicitly, one per Task Template; there is no way to dynamically enumerate "all Task Templates of Workflow Template X" from within a rule. See `_Engineering__Known_Limitations.md`.
- `Call` (Automation Rule field): selects a registered Webhook to invoke as part of the rule's actions.
- `Payload` (Automation Rule field): defines the JSON body sent to that Webhook, built from expressions.

## Naming

Task Template subjects referenced via `new(task, 'Subject')` or `tasks['Subject']` should be unique and descriptive per family/domain (e.g. `"Infra - Provision network"`, not `"Provision"`) — ambiguous resolution is a real risk if subjects repeat across templates.

## Related entries

- `_Engineering__Recipes.md` — practical use of `new(task, ...)`-adjacent patterns via the REST API when the expression language's constraints (no loop, no Phase/Workflow creation) make an in-rule solution insufficient.
- `_Engineering__Known_Limitations.md` — full detail and verification method for each constraint above.
