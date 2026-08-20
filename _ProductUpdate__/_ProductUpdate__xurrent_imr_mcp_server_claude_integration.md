---
title: "Your Incidents Are in Xurrent IMR. Now They're in Claude Too."
date: "April 14, 2026"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/xurrent-imr-mcp-server-claude-integration"
slug: "xurrent-imr-mcp-server-claude-integration"
---

# Your Incidents Are in Xurrent IMR. Now They're in Claude Too.

Incident responders live in two worlds: the alerting tool that pages them and the chat window where they coordinate. Context-switching between the two costs time, and during a critical outage, every second matters.

We built an MCP server for Xurrent IMR so that Claude can read your incident data directly. That means **you can ask plain-English questions about your on-call schedule, open incidents, and incident timelines without leaving the conversation.**

### What can you do with it?

Once the Xurrent IMR MCP server is connected, Claude has access to tools that map directly to your incident management data. Here are the kinds of questions you can ask:

📋
List & Filter
"Show me all critical incidents from the last month"
🔍
Search
"Find any incidents related to Grafana alerts"
📞
On-Call
"Who is on call for the SRE team right now?"
📖
Timeline
"Walk me through the timeline of incident #75"
### See it in action

We asked Claude to pull the latest incidents from our Xurrent IMR account and check who is currently on call for our SRE team. This is real data returned through the MCP connection:

claude.ai
>
Show me the 5 most recent incidents
Xurrent IMR → list_incidents
#
Title
Severity
Status
TTR
75
[Grafana] FIRING:1 TestAlert
Critical
Resolved
25s
74
[Grafana] FIRING:1 TestAlert
Critical
Resolved
5m
73
[Grafana] FIRING:1 TestAlert
Critical
Resolved
6m
70
[Grafana] Alert: TestAlert firing
Critical
Ack'd
38d+
66
[Grafana] Alert: TestAlert firing
Critical
Resolved
19s
Your 5 most recent incidents are all Grafana test alerts on the Application Monitoring service, assigned to the SRE team. Incident #70 is still in an acknowledged state and has been open for over 38 days.

>
Who is on call for SRE right now?
Xurrent IMR → get_current_on_call
The **SRE team** is using the Default Escalation Policy with three levels:

**Level 1** (immediate): Jacob Roscoe, Phil Christianson
**Level 2** (after 5 min): Tom G
**Level 3** (after 10 min): Bryan Patton

### Available tools

The MCP server exposes a focused set of read-only tools. Each one maps to a specific capability in your Xurrent IMR account:

- **list_incidents** – Query incidents with optional filters for status, severity, and date range.
- ‍**get_incident** – Retrieve full details for a single incident by number, including SLA info, priority, and timestamps.
- ‍**search_incidents** – Keyword search across incident titles and descriptions.
- ‍**list_incident_updates** – Get the chronological timeline of updates for any incident.
- ‍**list_teams** – List teams with optional member details.
- ‍**get_current_on_call** – See who is on call for a given team, broken down by escalation policy and level.

### Getting started

You can connect Xurrent IMR to Claude in under five minutes. Here is the setup:

1
Go to your Accounts page

Log in to your Xurrent IMR account and navigate to **Settings → Accounts**. This is where you manage API access and integrations for your organization.

2
Create an API key

Under the API section, generate a new API key. Give it a descriptive name like "Claude MCP Integration" so your team knows what it is for. Copy the key; you will need it in the next step.

3
Update your Claude config

Open your Claude Desktop config file and add the Xurrent IMR MCP server entry. On macOS, this file lives at `~/Library/Application Support/Claude/claude_desktop_config.json`:

{
"mcpServers"
: {
"xurrent-imr"
: {
"command"
:
"npx"
,
"args"
: [
"-y"
,
"@xurrent/imr-mcp-server"
],
"env"
: {
"XURRENT_IMR_API_KEY"
:
"your-api-key-here"
}
    }
  }
}
claude_desktop_config.json
{
"mcpServers"
: {
"xurrent-imr"
: {
"command"
:
"npx"
,
"args"
: [
"-y"
,
"@xurrent/imr-mcp-server"
],
"env"
: {
"XURRENT_IMR_API_KEY"
:
"your-api-key-here"
}
}
}
}
Restart Claude Desktop and you are ready to go. Ask Claude something like "What incidents do we have open?" and it will pull the answer directly from your Xurrent IMR account.

### What's next

This is a read-only integration today, perfect for quick lookups, on-call checks, and incident review. We are exploring write capabilities (creating incidents, adding timeline entries, acknowledging alerts) as the next step. If you have feedback or ideas for what you would want Claude to do with your incident data, we would love to hear from you.

#### Ready to try it?

Connect your Xurrent IMR account to Claude in under 5 minutes.

Get started with Xurrent IMR →
