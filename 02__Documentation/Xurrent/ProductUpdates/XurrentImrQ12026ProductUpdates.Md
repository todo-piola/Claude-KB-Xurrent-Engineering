---
title: "Xurrent IMR - Q1 2026 Product Updates"
date: "March 3, 2026"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/xurrent-imr-q1-2026-product-updates"
slug: "xurrent-imr-q1-2026-product-updates"
---

# Xurrent IMR - Q1 2026 Product Updates

> Note: We’re just getting started with 2026. This post is a living document, and we’ll keep adding new updates right here until the quarter ends on March 31st.

#### Your automations now fire on the exact moment that matters, not just when an incident opens.

Workflows support six incident-based triggers. You pick the event, set the conditions, and the automation runs the moment it happens — no manual step, no delay.

- Incident Created

- Incident Status Updated

- Incident Urgency Updated

- Incident Assigned To Updated

- Incident Team Priority Updated

- Incident SLA Updated

###### **Example**

> Priority changes to P0. Workflow fires instantly. Slack message and email go out to all stakeholders: "This incident has been escalated to P0. Immediate attention required." Nobody had to make a call or send a message manually.

Each trigger is fully configurable. Set conditions like "from anything to P0" or "urgency changes to critical during business hours." The workflow only fires when your conditions are met.

#### Checkmk Now Connects to Xurrent IMR

If your infrastructure monitoring runs on Checkmk, your alerts now flow directly into IMR without a workaround.

Checkmk alerts route to the right on-call team based on your escalation policies. Notifications go out via email, SMS, voice, Slack, Teams, and more. No alert gets missed.

You can go further with Alert Rules. Route specific Checkmk alerts to specific teams, suppress the noise that does not need a human, or auto-add responders and incident tasks when certain conditions hit.

[**Get started with the Checkmk Integration Guide →**](https://23298d9061312db0d759221cd16b9137.claudemcpcontent.com/mcp_apps?connect-src=https%3A%2F%2Fesm.sh+https%3A%2F%2Fcdnjs.cloudflare.com+https%3A%2F%2Fcdn.jsdelivr.net+https%3A%2F%2Funpkg.com&resource-src=https%3A%2F%2Fesm.sh+https%3A%2F%2Fcdnjs.cloudflare.com+https%3A%2F%2Fcdn.jsdelivr.net+https%3A%2F%2Funpkg.com+https%3A%2F%2Fassets.claude.ai&dev=true#)

#### Native Sentry Integration

Sentry deprecated webhook support for third-party tools. We built a proper native integration to replace it.

The old webhook-based setup is gone. The new native integration is faster to configure, more reliable, and officially supported going forward. If you were using Sentry with Xurrent IMR before, you need to reconnect.

Reconnecting takes under 2 minutes.

[**Set up the Sentry integration →**](https://23298d9061312db0d759221cd16b9137.claudemcpcontent.com/mcp_apps?connect-src=https%3A%2F%2Fesm.sh+https%3A%2F%2Fcdnjs.cloudflare.com+https%3A%2F%2Fcdn.jsdelivr.net+https%3A%2F%2Funpkg.com&resource-src=https%3A%2F%2Fesm.sh+https%3A%2F%2Fcdnjs.cloudflare.com+https%3A%2F%2Fcdn.jsdelivr.net+https%3A%2F%2Funpkg.com+https%3A%2F%2Fassets.claude.ai&dev=true#)

#### Workflow Permissions in Custom Roles

Non-admin team members can now create and edit workflows without needing full admin access.

Previously, only Admins and Owners could manage workflows. That created a bottleneck on teams where the person who knows the process best is not the admin. This change fixes that.

**1**. Go to Account, then Custom Roles

**2**. Create a role with View or Edit Workflows permissions

**3**. Assign the role to any team member

That person can now manage workflows independently. Admins stay in control of what access is granted. Everyone else gets to work without waiting for someone to do it for them.

#### Stop Guessing Who Just Paged You: Live Call Routing Clarity

We’ve all been there: It’s 3 AM, your phone rings, and you miss it while fumbling for your glasses. You open the incident summary to see who escalated the issue, and the caller ID is... _your own number_.

Playing detective during a SEV1 is the definition of toil. Previously, our Live Call Routing only displayed the assigned on-call agent's contact number, making it nearly impossible to quickly identify the actual stakeholder if a call was missed. We’ve overhauled the incident summary to give you instant context so you can skip the chat archaeology and get straight to debugging.

Now, your Live Call Routing summaries will automatically log:

- **The Caller:** The actual phone number of the person who initiated the panic.
- **The Dialed Helpline:** Exactly which routing number or service desk they hit.
- **Answered By:** The specific on-call agent who responded (if the call was picked up).

##### Earlier

##### Now

#### The LogicMonitor Integration

Having beautiful monitoring dashboards is great, but staring at glass doesn't fix a degraded cluster. If your monitoring signals aren't natively wired directly to your escalation paths, you are just generating noise and hurting your MTTR.

We are thrilled to release our native integration with LogicMonitor, bridging the gap between "something is broken" and "the right engineer is fixing it." You can now ingest LogicMonitor alerts directly into Xurrent IMR to drive a highly structured, automated incident response lifecycle.

Here is how it upgrades your workflow:

- **Zero-Touch Incident Creation:** When LogicMonitor detects an anomaly, Xurrent IMR automatically spins up an incident with all the attached context.
- **Precision Routing:** We suppress the noise and immediately notify the correct on-call engineer via their preferred channels (Slack, Microsoft Teams, SMS, voice, or push notification).
- **Failsafe Escalations:** If the primary engineer is tied up, Xurrent IMR systematically runs your escalation policies until the issue is officially acknowledged. No critical alert gets left behind.

📖 Ready to wire it up? [Read the LogicMonitor Integration Docs Here](https://zenduty.com/docs/logicmonitor-integration/)

#### Stop Sending Noise to Your Other Tools

We are kicking off 2026 by giving you more control over your integrations. We know the pain: you set up an integration to send incident data to Jira or Slack, but it keeps firing off updates you don't care about. You end up with "Resolved" notifications clogging up your channels when you really only wanted to know when things were on fire.

We’ve updated Outgoing Rules to support Incident Status as a condition. Previously, you could filter by title or urgency, but now you can be precise about the _state_ of the incident. You can set a rule that says, "Only send this data to Zendesk if the Status is NOT Resolved." It’s a small tweak that saves your team from notification fatigue and keeps your downstream tools clean.

#### Reports That Actually Tell the Whole Story

If you spend time in our Analytics tab, you know that data is only useful if it has context. You told us that downloading reports felt like getting half the story—you had the numbers, but you missed the notes, the tags, and you had to do mental math to figure out the time. We fixed all three of those annoyances in one go.

1. Context is King (Incident Notes)Previously, your downloaded reports were missing the actual human conversation. Now, Incident Notes are included as a column in your export. This means you can review the responder’s commentary and the "why" behind the incident directly in the report, making post-mortems and retrospectives much faster.

2. Slice and Dice (Incident Tags)We’ve also added Incident Tags as a dedicated column. If you tag incidents by environment (like "prod" vs "staging") or by customer name, those tags now show up in your CSV. This makes it incredibly easy to spot trends—like realizing that 80% of your alerts last week came from a single buggy beta feature.

3. Stop Doing Math (Timezone Awareness)Finally, we fixed the most annoying part of reporting: UTC timestamps. In the past, every report used Universal Time, forcing you to manually convert hours in your head or in Excel. Now, downloaded reports automatically respect the Timezone in your User Profile. If you are in New York, your report is in EST. No more mental math required.

‍
