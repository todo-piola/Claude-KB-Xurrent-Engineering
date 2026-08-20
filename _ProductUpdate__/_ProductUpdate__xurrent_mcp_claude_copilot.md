---
title: "Xurrent, now in Claude & Copilot. Meet the Xurrent MCP server."
date: "May 14, 2026"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/xurrent-mcp-claude-copilot"
slug: "xurrent-mcp-claude-copilot"
---

# Xurrent, now in Claude & Copilot. Meet the Xurrent MCP server.

Your service desk has a lot of context locked inside it. Open requests, assignments, knowledge articles, the queue you've been meaning to triage all morning. Useful information, but it lives in tabs and tickets, not where you actually do your thinking.

We're proud to announce that [the Xurrent MCP server](https://www.xurrent.com/blog/xurrent-mcp) is generally available to all customers. Connect it to your AI client of choice and Xurrent becomes part of the conversation. Ask what's in your inbox, summarize a request, pull up the right knowledge article, kick off a service request from a template, check whether a service is healthy. The data and the actions are right there.

### What you can do with it

The MCP server exposes the parts of Xurrent that show up in everyday work. Some of what's available on day one:

- Triage your inbox. "What's on my plate today, and what should I look at first?"
- Summarize a request, a task, or a problem record so you can catch up in seconds
- Search the knowledge base and get a usable summary back, not a list of links
- Find active requests by owner, age, or service so nothing slips
- Start a new request from a template
- Check service availability across the platforms your team depends on
- Browse agile board items and project tasks

Want to see everything the server exposes in your tenant, just ask the assistant to _list tools_. The available set surfaces automatically.

### Getting started

Setup takes a few minutes: generate a PAT in your Xurrent account, point your AI client at `https://mcp.xurrent.com/mcp`, paste the token, restart.

Full step-by-step instructions, including the Claude Desktop config snippet, are [in the help article](https://www.xurrent.com/help/mcp).

### Want even more? Pair it with Xurrent IMR.

If you're using Xurrent IMR for incident management, there's a second MCP server you'll want connected too. With [the IMR MCP server](https://www.xurrent.com/product-updates/xurrent-imr-mcp-server-claude-integration), Claude (or Copilot) can pull live incident data, on-call schedules, and timelines into the same conversation, so you can ask "who's on call for SRE right now?" or "walk me through the timeline of incident #75" without leaving your chat window.

The real power shows up when you connect both. Picture a major incident: you ask Claude (or Copilot) to walk you through the timeline of the IMR incident, identify which CIs and services were affected, then open a problem record in ITSM linked back to the incident, and surface any related knowledge articles the team should review before the postmortem. One conversation, two systems, no tab-switching.

Together, the two MCP servers cover the full ITxM picture: service operations on one side, incident response on the other, both reachable from a single conversation.

### Try it

We'd love to hear what works, what doesn't, and what you want to do next. Give it a spin and let us know.
