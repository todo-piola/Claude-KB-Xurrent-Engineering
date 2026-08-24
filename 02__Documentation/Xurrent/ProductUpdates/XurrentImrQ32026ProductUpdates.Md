---
title: "Xurrent IMR - Q3 2026 Product Updates"
date: "August 3, 2026"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/xurrent-imr---q3-2026-product-updates"
slug: "xurrent-imr---q3-2026-product-updates"
---

# Xurrent IMR - Q3 2026 Product Updates

### **Percentiles in Analytics is here**

Every metric in Analytics used to be a mean. And means lie when incident data is skewed. One 10-day outage quietly drags your MTTR up. A handful of auto-resolved blips drag it down. The number you report to leadership stops matching what your on-call engineers actually lived through.

You can now switch any metric between Mean, P75, P95, and P99 from the aggregation dropdown. Total Incidents, MTTA, MTTR, all of it.

‍

Want the resolution time 95% of incidents actually fall under? That's P95.

Percentiles work across Overview, Teams, Services, and Users. Now you can read a team's MTTA and MTTR the same way you'd read request latency in your observability stack: by the tail, not the average.

### **Custom Incident Form: build the form each incident actually needs**

A Security incident needs CVE IDs and compliance frameworks. A Sev0 outage needs blast radius, customer impact, and a war room link. Forcing both into the same rigid form means responders capture too little, right when detail matters most.

The new Custom Incident Form lets you decide what gets captured for each kind of incident. Define custom fields once (Impact Summary, CVE ID, Region Affected, Revenue Impact, anything your team tracks), then group them into incident types like Alert, Security Incident, or Major Incident.

Responders pick a type at creation. The form reshapes on the spot.

Head to Account Settings > Custom Incident Form to set it up.

[[Set it up →]](https://www.xurrent.com/imr-help/custom-incident-form)

### **Root Cause Agent: the first five minutes of investigation, already done**

When an incident hits, the clock starts and so does the scramble. Digging through dashboards. Scrolling old Slack threads. Trying to remember if you've seen this before.

Sera's new Root Cause Hypothesis Agent does that investigation for you. Open any incident, click Investigate (or trigger it right from the incident's Slack channel). Within seconds, Sera returns:

- Probable root cause
- Confidence level
- Evidence
- Mitigation steps

Sera works by reading your alert payload, finding the most similar past incidents your team has resolved, and pulling the postmortems and Slack threads from those. Signal from your own history, surfaced when you need it.

##### **_Coming soon_**

Sera's about to get sharper.

GitHub. Sera will cross-reference recent PRs and deploys against the incident timeline, so you'll know if a code or config change is the likely culprit.

Datadog, Grafana, Sentry. Connect your observability stack and every investigation gets richer signal to work from.
