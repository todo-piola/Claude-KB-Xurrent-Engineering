# Xurrent Engineering Knowledge Base

Version-controlled source of truth for the curated Xurrent engineering knowledge
base (Automation Rules patterns, known limitations, debugging techniques,
recipes, ITSM solution patterns, and integrations notes).

## Files

| File | Scope |
|---|---|
| `00__ProjectInstructions/KnowledgeIndex.md` | Taxonomy / index — where each type of finding belongs |
| `01__Platform/AutomationRules.md` | Automation Rule execution behaviour, operators, constraints |
| `01__Platform/ReportingAnalytics.md` | Native behaviour of Analytics console views (Change Calendar, Reports, Dashboards) |
| `03__Engineering/KnownLimitations.md` | Verified platform limitations, gotchas, workarounds |
| `03__Engineering/Debugging.md` | Debugging methodology and techniques |
| `03__Engineering/Recipes.md` | Reusable implementation patterns |
| `03__Engineering/SolutionPatterns.md` | ITSM process design patterns |
| `03__Engineering/Integrations/Webhooks.md` | Webhook integration notes |

## Recommended workflow

1. Work through **Claude Code** (Desktop, terminal, or VS Code) pointed at a
   local clone of this repo. Each finding gets committed with a clear message
   — that commit history is the audit trail.
2. This repo is the canonical source. The Claude.ai **Project Knowledge Base**
   is a secondary, queryable mirror: after committing changes here, re-upload
   only the files that changed to the Project (replacing the old version) so
   in-chat search (`project_knowledge_search`) stays current.
3. Commit messages should name the finding, not just "update" — e.g.
   `Add: Automation Rules execute as account owner (completion team/member assignment)`.

## Status

Baseline import from the Claude Project Knowledge Base on 2026-08-19. History
starts here — earlier changes are not retroactively reconstructed.
