# Engineering/Integrations/Webhooks.md

Confirmed platform capabilities for building outbound integrations from Xurrent via Webhooks, and the authentication mechanisms available to external services calling back into the Xurrent API.

---

## Purpose

Webhooks are how Xurrent notifies an external service in near real-time that something happened, so that service can react — including calling back into the Xurrent REST API to perform further changes (e.g. the pattern in `_Engineering__Recipes.md`, where a Webhook triggers an external service to inject Tasks/Phases into a Workflow).

## Triggering a Webhook from an Automation Rule

An Automation Rule can invoke a registered Webhook directly as part of its actions:

- `Call` (Automation Rule field): selects which registered Webhook to invoke.
- `Payload` (Automation Rule field): defines the JSON body sent to that Webhook, built from expressions (e.g. `{ workflow_id: workflow.id, ... }`).

## Authentication

### Personal Access Tokens (PAT)

- Generated from *My Profile → Personal Access Tokens → Generate token*.
- Scoped per model (e.g. `workflow`, `task`, `workflow-template`).
- Confirmed: the `/me` endpoint specifically requires a separate `me` scope — easy to miss when a token is scoped only for the target business models.
- Suitable for personal/manual testing; not recommended as the identity for a production service (see below).
- A PAT's scope and account actions are fixed at creation time — editing them afterwards does not change what the existing token can do. See `Engineering/KnownLimitations.md` — "Personal Access Token permission changes do not apply retroactively to the existing token".

### OAuth Client Credentials Grant

Confirmed to exist as the platform's mechanism for application/service identities, as opposed to a person's own Personal Access Token. Recommended for production integrations instead of a personal PAT, scoped minimally to only the models the integration touches.

### Account selection

The account context is selected via the `X-Xurrent-Account` header on every request — not via a subdomain in the request path. The API host itself (`baseUrl`) stays constant regardless of which account is being addressed.

## Verifying Webhook Authenticity

Xurrent can cryptographically sign webhook payloads as a JWT via a **Webhook Policy** (*Settings → Webhook Policies*). The receiving service should verify the signature using the policy's public key before trusting the payload contents. This is the officially documented mechanism for confirming a webhook call genuinely originated from the expected Xurrent account.

## Reliability

Xurrent **automatically disables a Webhook after 20 consecutive failures spanning more than a week**. Independent monitoring/alerting on the receiving service's side is advisable — this can otherwise fail silently, with no proactive notification beyond what's visible in the Xurrent Webhooks admin screen.

## Known Limitations

See `Engineering/KnownLimitations.md`, "API host for legacy-branded ('4me.qa') domain accounts may differ from the documented Service URL table" — relevant when configuring the callback endpoint's own outbound calls back to Xurrent.

## Related entries

- `Engineering/Recipes.md` — end-to-end example of a Webhook-triggered call sequence.
- `Platform/AutomationRules.md` — `Call`/`Payload` fields in full Automation Rule context.
