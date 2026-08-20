# Xurrent Engineering Knowledge Base

Version-controlled source of truth for the curated Xurrent engineering knowledge
base (Automation Rules patterns, known limitations, debugging techniques,
recipes, ITSM solution patterns, and integrations notes).

This repo does **not** include the `_API__*.md` files (static mirror of the
official Xurrent developer documentation). Those are reference material, not
content edited through conversations, so they don't need commit history — they
can continue to live as-is in the Claude Project's Knowledge Base.

## Files

| File | Scope |
|---|---|
| `00_Knowledge_Index.md` | Taxonomy / index — where each type of finding belongs |
| `_Platform__Automation_Rules.md` | Automation Rule execution behaviour, operators, constraints |
| `_Engineering__Known_Limitations.md` | Verified platform limitations, gotchas, workarounds |
| `_Engineering__Debugging.md` | Debugging methodology and techniques |
| `_Engineering__Recipes.md` | Reusable implementation patterns |
| `_Engineering__ITSM_Solution_Patterns.md` | ITSM process design patterns |
| `_Integrations__Webhooks.md` | Webhook integration notes |

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
