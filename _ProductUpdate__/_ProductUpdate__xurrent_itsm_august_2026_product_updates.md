---
title: "Xurrent ITSM - August 2026 Product Updates"
date: "August 6, 2026"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/xurrent-itsm-august-2026-product-updates"
slug: "xurrent-itsm-august-2026-product-updates"
---

# Xurrent ITSM - August 2026 Product Updates

This post is a living document, updated throughout the month as new product releases roll out. Each update listed here is released to our QA environment on the date shown and typically promoted to production the following week. Along the way, customers can review changes, share feedback, and help shape what ships next. Xurrent delivers product updates on a weekly cadence to keep enhancements moving continuously.

### August 6, 2026

#### Knowledge Articles: Automatic Translation

Knowledge articles can now be translated automatically into every language enabled in the account's "Supported languages" list. Enable the "Automatically translate knowledge articles" setting under Self Service Settings and end users see articles in their own language.

Automatically translated content is marked with a notice so readers know the text was translated by machine. Hand-written translations always take precedence; when the source article is edited, the affected manual translations are marked outdated and the automatic translation takes over until they are refreshed. Authors can also declare the language an article is written in: the "Language" field on the article form is now an editable picker.

Previously, every language version had to be translated by hand, so articles in less common languages were often missing or out of date.

Automatic translations do not appear in Settings > Translations and cannot be edited. The "Language" field becomes read-only once an article has translations.

#### Tags: Merge Duplicate Tags

Tags can now be merged. Select a tag's Actions menu and choose Merge to fold it into another tag, or select multiple tags in the grid and merge them in one action, choosing which tag survives.

Records carrying the merged tags are re-tagged to the surviving tag, the audit trail records the change, and the merged tags are disabled. Previously, duplicate tags created by typos or inconsistent naming ("UIX designer" vs "UX Designer") could only be disabled, which removed them from records without consolidating them. Merging requires account administrator access; specialists can rename tags but do not see the merge action. A record that already carries the surviving tag is not double-counted.

#### Dashboards: Refresh and Timestamp

All dashboards now include a refresh control that recalculates tile figures on demand. Unlike the other enhancements in this update, this change has been released directly to production and is available now.

A timestamp in the dashboard header shows when the figures were last calculated, so it is always clear how current the data is. The r684 release, in production since July 23, lengthened the dashboard tile caching interval from 5 to 20 minutes as part of platform performance work. The automatic 20 minute interval remains the default. Reports opened directly continue to query live data and are unaffected by the dashboard cache.

#### Lookup Pickers: Exact Matches First

When a search in a lookup picker exactly matches a record's indexed field value, that record now appears at the top of the dropdown. Typing a full identifier like "ABCD 1234-1234" surfaces that record first instead of several rows down among other "ABCD" prefix matches. Comparison is case-insensitive and ignores leading and trailing whitespace; all partial matches remain in the list below, in their existing order.

Previously, a record whose value was spelled out in full could be buried below prefix matches, forcing the user to scan the list for the record they had already fully typed. Exact matches on a related record's fields (a site name in the Configuration item picker, an organization name in the People picker) do not promote the linked records. The "find reference" (#) picker in note editors keeps its existing ordering.

#### Data Integrity Reports: Counts on the Overview

The Data Integrity Reports page now lists every report in a single sortable table with a "Report Count" column showing how many records currently fail each check, sorted largest first by default.

The table supports name search, a category filter, and clicking either the report name or the count to open the report. Previously, the page was a static list of links, so establishing the state of an account meant opening each of the 40 reports individually. Counts reflect only records the signed-in user is permitted to see.

#### Request Templates and Knowledge Articles: "Times Applied" Column

The number of times a request template or knowledge article has been applied is now available as a "Times Applied" column in list views, selectable from "Customize Columns...".

The column is sortable, filterable with the standard numeric operators, and included in exports. The same all-time value appears on the record and is exposed read-only through the REST and GraphQL APIs on both record types. Previously, the only on-screen usage signal for knowledge articles was "Times Viewed", which shows whether an article was found but not whether it resolved anything. The count is cumulative over the record's lifetime and is distinct from the "Usage - Last 90 days" section.

#### Approvals: External Delegate Confirmation

Delegating an approval to a person outside the organization now asks for confirmation first, naming the selected person's name, organization, and primary email address.

Cancelling leaves the approval untouched, with no audit entry and no notification sent. Delegating to a colleague is unchanged and takes no extra click. Previously, selecting a delegate reassigned the approval immediately, so a single mis-click could hand an approval and its request context to an outside contact. The confirmation applies in Self Service and the specialist interface, on approval tasks and approval project tasks. It is a mistake-prevention prompt, not an access control: accounts that want external people excluded entirely from delegation should continue to use Strong Privacy.

#### Automation Rules: Tag Support

Automation rules can now read and set tags on Problem, Workflow, Task, Project, and Project Task records, using the same properties and actions available on Requests. Previously, tag automation was limited to Requests, so tags on other record types could only be managed manually. Tag lookups remain scoped to the record's account; a rule that attempts to apply a tag from another account is reported as a failed rule execution.

#### Xurrent MCP: Settings Realignment

MCP server access is now controlled by the "Xurrent +AI" account setting. When MCP is unavailable, the error names "Xurrent +AI" as the setting to enable. Previously, MCP was gated on the Self Service setting "Enable Sera AI", which exists to control the Virtual Agent and has no functional relationship to MCP. "Enable Sera AI" now controls the Virtual Agent only.

#### Currencies: RSD Symbol

Serbian Dinar amounts are now labelled with the ISO code "RSD" wherever a currency symbol appears, including the currency dropdown on the Amount field. Previously, the dropdown showed the Cyrillic abbreviation "дин.", which made the option hard to recognize. Several currencies already use their three-letter code as their symbol, so this follows the existing convention. Amounts, conversions, and totals are unchanged; only the label differs.
