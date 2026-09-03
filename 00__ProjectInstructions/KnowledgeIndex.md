# Xurrent Engineering Knowledge Base

## Purpose

This document provides the conceptual map of the Xurrent Engineering Knowledge Base.

It helps identify where different types of information are stored and how the available knowledge should be used.

This document is an index, not a replacement for the underlying documentation.

**Last synchronized:** 2026-09-03 — added `Platform/ReportingAnalytics.md` (Change Calendar visibility requirements) and corresponding `Engineering/KnownLimitations.md` entry.


## Where This Lives

This Knowledge Base currently exists in two locations that must stay in sync:

- **Git repository** (canonical source for the curated engineering files below). See `README.md` for the file list and the recommended Claude Code workflow, and `CLAUDE.md` for the operating rules an assistant should follow when editing this repo.
- **Claude.ai Project Knowledge Base** — holds the same curated files as a queryable mirror (for in-chat search), **plus** the full `API*.md` official API documentation mirror.

This index applies to both locations equally. Workflow details (commit discipline, confirmation rules) live in `CLAUDE.md` and the Project's custom instructions respectively, not here — see section 10.


## 1. Knowledge Sources

The project contains several categories of knowledge.

### 1.1 Official Xurrent Documentation

Official Xurrent documentation is the primary source of truth.

It includes:

- Xurrent Help documentation
- Xurrent developer/API documentation
- Official field documentation
- Official Automation Rule documentation
- Official UI Extension documentation
- Official Workflow and Task Template documentation

Official API documentation is stored as individual Markdown files using the naming convention:

`02__Documentation/Xurrent/API/<Example_ElementExample>.md`

Example:

`02__Documentation/Xurrent/API/AgileBoards_Audit.md`


### 1.2 Verified Engineering Knowledge

Knowledge derived from validated implementation work.

This includes:

- Reusable Automation Rule patterns
- UI Extension patterns
- Workflow design patterns
- API implementation patterns
- Integration patterns
- Debugging techniques
- Known platform limitations
- Regex patterns

Verified engineering knowledge must not override official documentation without explicitly identifying the discrepancy.


### 1.3 Observed Platform Behaviour

Some Xurrent behaviour may be verified through actual execution in an Xurrent environment without being explicitly documented.

Such information should be treated as:

**[Observed]**

It should not automatically be described as an official Xurrent limitation.

Where possible, document:

- Xurrent version/date
- Object
- Configuration
- Reproduction steps
- Actual result
- Expected result
- Workaround

## 2. Platform Knowledge

### 2.1 Architecture

File: `Platform/Architecture.md`
**Status:** 🕳 Not yet created

Contains:

- Xurrent object model
- Record types
- Relationships
- Accounts and subdomains
- Permissions
- Assignment model
- Workflow model
- General platform concepts

Use this when reasoning about how Xurrent objects relate to each other.


### 2.2 Automation Rules

File: `Platform/AutomationRules.md`
**Status:** ✅ Exists

Contains:

- Automation Rule structure
- Triggers
- Conditions
- Expressions
- Updates
- Expression naming
- Execution behaviour (including identity/permissions the Rule executes as)
- Recursion considerations
- Reusable automation patterns
- Known Automation Rule constraints
- Request/Workflow completion team & member assignment rules


### 2.3 Expression Language

File: `Platform/ExpressionLanguage.md`
**Status:** 🕳 Not yet created

Contains:

- Collections
- select
- reject
- map
- first
- last
- join
- conditionals
- comparison operators
- boolean operators
- nil handling
- string manipulation
- type behaviour
- verified expression examples

Treat the Xurrent expression language as distinct from general Ruby.


### 2.4 Workflow Templates

File: `Platform/WorkflowTemplates.md`
**Status:** 🕳 Not yet created

Contains:

- Workflow architecture
- Phases
- Tasks
- Dependencies
- Approvals
- Assignment behaviour
- Completion behaviour
- Rejection behaviour
- Automation interaction

Note: until this file exists, native Workflow completion/rejection behaviour findings are documented in `Platform/AutomationRules.md` (when the finding concerns Automation Rule interaction) or `Engineering/SolutionPatterns.md` (when the finding concerns approval process design) — see those files' own scope. Move them here once this file is created and enough content exists to justify the split.


### 2.5 Task Templates

File: `Platform/TaskTemplates.md`
**Status:** 🕳 Not yet created

Contains:

- Task Template configuration
- Assignment
- Approvals
- Instructions
- Notes
- UI Extensions
- Automation interaction
- Reusable Task Template patterns


### 2.6 UI Extensions

File: `Platform/UIExtensions.md`
**Status:** 🕳 Not yet created

Contains:

- HTML
- JavaScript
- CSS
- Xurrent UI Extension APIs
- Hooks
- Field manipulation
- Readonly behaviour
- Required fields
- Visibility
- Dynamic values
- Event handling
- Reusable UI Extension patterns


### 2.7 API

Official API documentation is stored as individual files.

Official API documentation is stored as individual Markdown files using the naming convention:

Example:

`02__Documentation/Xurrent/API/<Example_ElementExample>.md`

**Status:** ✅ Exists

Use the most specific API document available rather than relying on assumptions.


## 3. Engineering Knowledge

### 3.1 Recipes

File: `Engineering/Recipes.md`
**Status:** ✅ Exists

Contains short, reusable solutions.

Examples:

- Get assigned Workflow tasks
- Get task subjects
- Get assigned teams
- Get first Request of a Workflow
- Update Request from Workflow
- Update Workflow from Task
- Common Automation Rule patterns
- Common UI Extension patterns
- Common API patterns

Recipes should favour concise, copy-ready implementations.


### 3.2 Known Limitations

File: `Engineering/KnownLimitations.md`
**Status:** ✅ Exists

Contains verified or observed limitations.

Each entry should ideally contain:

**Problem** — What is being attempted?
**Expected behaviour** — What should happen?
**Actual behaviour** — What actually happens?
**Verification** — How was it tested?
**Status** — `[Confirmed]` / `[Observed]` / `[Hypothesis]` / `[Unknown]`
**Workaround** — What solution is available?
**Notes** — Version, date, environment, or cross-references to related entries in other files.


### 3.3 Debugging

File: `Engineering/Debugging.md`
**Status:** ✅ Exists

Contains:

- Expression debugging
- Automation Rule debugging
- Rule Execution Viewer techniques
- UI Extension debugging
- API debugging
- Common parser errors
- Type issues
- nil handling
- Assignment issues
- Workflow execution issues
- Troubleshooting methodology


### 3.4 Regex Cookbook

File: `Engineering/RegexCookbook.md`
**Status:** 🕳 Not yet created

Contains reusable Ruby-compatible regular expressions where applicable.

Examples:

- Remove JSON-style brackets
- Remove quotation marks
- Extract IDs
- Extract values
- Replace delimiters
- Validate common formats

Regex behaviour must be verified against the actual Xurrent function that consumes the expression.

Do not assume that Ruby regex support means every Ruby regex method or replacement syntax is supported by Xurrent.


## 4. Integrations

Category prefix: `Integrations/<Topic>.md` — one file per integration/topic, following the same pattern as every other category, rather than a single catch-all file.

| File | Status |
|---|---|
| `Integrations/Webhooks.md` | ✅ Exists |
| `Integrations/Lansweeper.md` | 🕳 Not yet created |
| `Integrations/iPaaS.md` | 🕳 Not yet created |
| `Integrations/OAuth.md` | 🕳 Not yet created |

Create a new `Integrations/<Topic>.md` file only once there is verified, reusable content for that specific integration — do not pre-create empty files.

Each integration entry should document:

- Purpose
- Source
- Target
- Authentication
- Data flow
- Mapping
- Trigger
- Error handling
- Retry behaviour
- Known limitations


## 5. Reporting and Analytics

File: `Platform/ReportingAnalytics.md`
**Status:** ✅ Exists

Contains:

- Custom Views
- Reports
- KPIs
- Calculated values
- Date/time calculations
- Grouping limitations
- Dashboard design
- Reporting workarounds

Document limitations explicitly, especially when a calculated value cannot be grouped, rounded or converted because of its underlying Xurrent data type.


## 6. Custom Collections and Views

File: `Platform/CustomCollectionsViews.md`
**Status:** 🕳 Not yet created

Contains:

- Custom Views
- Custom Collections
- Collection elements
- Directory-related configuration
- Naming conventions
- Reference identifiers
- Service-related collections
- Non-Service custom collection designs

Document the actual location and ownership of the collection carefully, because Xurrent account/subdomain placement affects visibility and usability.


## 7. ITSM / ITIL Solution Design

File: `Engineering/SolutionPatterns.md`
**Status:** ✅ Exists

Contains solution design patterns for:

- Incident Management
- Request Fulfillment
- Change Management
- Emergency Change
- Major Incident
- Problem Management
- Approval processes
- CAB / eCAB
- Workflow governance
- Digital / business processes

Always distinguish between:

1. ITIL guidance
2. Common industry practice
3. Xurrent capability
4. Customer-specific design


## 8. Naming and Conventions

File: `Engineering/Conventions.md`
**Status:** 🕳 Not yet created

Contains project conventions for:

- Automation Rule names
- Expression names
- Task names
- Task Template names
- Workflow Template names
- Custom Fields
- UI Extensions
- Custom Collections
- Views
- Integrations
- Documentation
- Git commit messages (see also `CLAUDE.md` — "Commit Discipline")

Use professional, descriptive English names.


## 9. Knowledge Quality

Knowledge should be classified according to confidence.

**[Confirmed]** — Supported by official documentation or directly verified through authoritative sources.
**[Observed]** — Verified through actual Xurrent execution but not necessarily documented.
**[Hypothesis]** — Plausible explanation requiring further validation.
**[Unknown]** — No reliable confirmation has been found.

Never promote `[Hypothesis]` or `[Unknown]` information to `[Confirmed]` without verification. A finding that is later corrected (e.g. an initial theory disproven by a second data point) should have the corrected version documented — not both versions presented as equally valid.


## 10. Knowledge Maintenance

When a reusable discovery is made:

1. Verify it.
2. Determine whether it is reusable.
3. Identify the correct knowledge category using this index — create a not-yet-created file from the taxonomy above rather than inventing a new category; only add a genuinely new category here if nothing above fits.
4. Document the behaviour concisely, in the existing format of the target file.
5. Include the verification method.
6. Include version/date information when relevant.
7. Mark the confidence level.

Avoid documenting temporary debugging details that have no future value.

Avoid duplicating the same knowledge across multiple files — cross-reference instead (see the "Notes" convention in section 3.2).

This section states the *principle*. The confirm-before-writing workflow itself is enforced by, and detailed in:
- the Claude.ai Project's custom instructions ("Human-in-the-Loop for Memory, Knowledge Base and Instructions") when working in chat, and
- `CLAUDE.md`'s "Human-in-the-Loop for Repository Changes" and "Commit Discipline" sections when working in the git repo via Claude Code.


## 11. Current Project Context

The Knowledge Base now exists as a git repository (canonical for the curated engineering files) mirrored into a Claude.ai Project (which additionally holds the full `API*.md` reference mirror — see section 1.1).

Of the taxonomy above, the following files currently exist with real content: `Platform/AutomationRules.md`, `Platform/ReportingAnalytics.md`, `Engineering/Recipes.md`, `Engineering/KnownLimitations.md`, `Engineering/Debugging.md`, `Engineering/SolutionPatterns.md`, `Integrations/Webhooks.md`. Every other file listed in this index is a reserved taxonomy slot, not yet created — check the **Status** field before assuming a file has content or citing it.

The project should continue to evolve into a reusable Xurrent engineering knowledge base rather than a chronological archive of conversations. When updating this index (new file created, category added, convention changed), update the "Last synchronized" date at the top.
