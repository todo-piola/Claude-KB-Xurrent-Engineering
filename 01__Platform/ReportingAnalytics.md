# Platform/ReportingAnalytics.md

Native behaviour of Xurrent's Analytics console features (Dashboards, Reports, Custom Views, Change Calendar). Each entry documents how a specific view or report determines what data it surfaces — not how to build a report, but the underlying rules governing visibility, scoping, and calculation. Append new entries below following the same structure.

---

## Change Calendar — Visibility Requirements

### Summary

A Task appears in the Change Calendar (Analytics console → Change Calendar) only when **all** of the following are true:

1. `Task.category` = `Implementation`
2. The Task belongs to a Workflow (i.e. it is a Change task, not a standalone Task)
3. The Task is `linked` to a Service Instance

If any of these is missing, the Task will not be rendered on the calendar — regardless of scheduling fields such as `start_at` or `planned_duration`.

### Status

[Confirmed] — documented across multiple official Xurrent Product Updates.

### Detail

**Category = Implementation** — the Change Calendar only presents Tasks whose category is `Implementation`; this is why the "Category" filter is deliberately absent from the Change Calendar's filter panel (it would be redundant).

**Service Instance link** — the least obvious requirement. Even a Task with `category = Implementation` that belongs to a Change will **not** render if it has no linked Service Instance. This is explicitly stated by Xurrent: the task is only visible in the Change Calendar when it is related to a service instance.

**Service filter behaviour** — the "Service" filter in the Change Calendar is broader than in ordinary task views/reports: it matches Tasks whose Change is linked to the selected Service, *or* whose linked Service Instance belongs to the selected Service. This differs from the "Service" filter in Records console task views, which only looks at the Change's Service.

**Conflict rendering** — Tasks that don't match the active filter, but conflict (same assignee, or related Service Instance in an overlapping time window) with a Task that does match, are still rendered — shown semi-transparent rather than hidden.

### Verification method

Official Xurrent Product Updates (xurrent.com/product-updates): "Advanced Change Calendar Filters" (2020-06-17), "Change Calendar Improvements", "Two More Change Calendar Enhancements".

### Notes

- Not yet verified: which field(s) position the Task's bar on the timeline (`start_at` + `planned_duration` is the working hypothesis — [Hypothesis], not confirmed against official docs or live testing).
- Cross-reference: `Engineering/KnownLimitations.md` → "Task Not Appearing in Change Calendar Despite Category = Implementation".
- Relevant to: Emergency Change workflow design (six-task sequence) — the Implementation-category task(s) in that workflow must carry a Service Instance link if visibility on the Change Calendar is required for ECAB/scheduling purposes.
