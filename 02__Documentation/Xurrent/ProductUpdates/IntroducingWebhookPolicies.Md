---
title: "Introducing Webhook Policies"
date: "July 20, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-webhook-policies"
slug: "introducing-webhook-policies"
---

# Introducing Webhook Policies

Xurrent administrators are now able to add an extra layer of security to the payloads their [webhooks](https://developer.xurrent.com/v1/webhooks/) send out.  They can do this by creating a webhook policy in the ‘Webhook Policies’ section of the Settings console.

A webhook policy defines the signing algorithm that Xurrent has to use to sign the payload of outbound webhook requests.  By getting Xurrent to sign each payload, the receiver can verify whether a payload was really created and signed by Xurrent and not by some other party.

Multiple webhooks can be related to a webhook policy.

After a new webhook policy is saved for the first time, the administrator has a one-time opportunity to download its public key.  The hosts receiving payloads from the related webhooks will need this public key to decrypt the payloads from these webhooks.

Because it is possible to create multiple webhook policies in a Xurrent account, administrators can create a separate webhook policy for each service provider to which their organization has outsourced the processing of webhooks.
