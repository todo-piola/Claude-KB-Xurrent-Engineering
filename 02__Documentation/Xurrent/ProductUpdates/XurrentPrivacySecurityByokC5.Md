---
title: "Xurrent Launches BYOK Security & C5 Compliance"
date: "January 15, 2025"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/xurrent-privacy-security-byok-c5"
slug: "xurrent-privacy-security-byok-c5"
---

# Xurrent Launches BYOK Security & C5 Compliance

_[UPDATED FEBRUARY 2025]_

From its inception over a decade ago, Xurrent has maintained uncompromising standards in privacy, security, and compliance excellence.

From the beginning of the European Union’s [General Data Protection Regulation (GDPR](https://www.xurrent.com/gdpr-compliance)) in 2018 through the present day, Xurrent has been a leader in providing world-class capabilities to help our customers remain compliant. Internally, we recertificated [ISO 27001:2022 and ISO 27018 standards](https://www.xurrent.com/press-release/xurrent-achieves-iso-270012022-and-iso-27018-recertification), further signaling our steadfast commitment to security and privacy.

As a security-first company, we continue to spearhead new developments and technologies.

### BYOK and C5 have arrived at Xurrent

**Since January 1, 2025, we now have “Bring Your Own Key” (BYOK) capability available in our cloud data center.**

Starting this month, customers can encrypt their data using their own private keys inside our AWS cloud deployment.

BYOK, we believe, will become table stakes for SaaS organizations. With Xurrent adding it now, it further establishes our position as a market leader — several steps ahead of our peers, ideal for those looking for a truly secure ITSM platform.

Continuing to pave the way for security compliance, the European Union and its member states are setting the bar high. The Cloud Computing Compliance Criteria Catalog (C5) will soon be mandatory for SaaS providers.

**_UPDATE: As of February 2025, Xurrent has been granted approval for C5._**

So how does this all work?

### The nitty-gritty (technical side) of BYOK and C5

First, Xurrent is a certified Amazon Partner, and our cloud, hosted within AWS, utilizes [AWS Key Management Service (KMS)](https://aws.amazon.com/kms/)as the core component for BYOK implementation. AWS KMS provides a secure and scalable platform for managing encryption keys, including the option for customers to bring their _own_ keys … BYOK, if you will.

Let’s get a bit more techy.

With BYOK, Xurrent customers can create their own Amazon account and generate (and manage) their Customer Master Keys (CMKs) within AWS KMS. These CMKs are used to encrypt and decrypt customer data stored within the Xurrent Platform. The customer — and this is the key (pun intended) — defines fine-grained access control policies within AWS Identity and Access Management (IAM) to govern access to the CMKs. This ensures that only authorized services (i.e., the Xurrent Platform) can use the keys for encryption and decryption operations.

Further, customers can configure AWS CloudTrail and Amazon CloudWatch to monitor key usage and security-related events within AWS KMS. This enables real-time detection of unauthorized access attempts or suspicious activities. Customers have complete control to revoke keys, after which any encrypted data with those keys becomes unavailable/unreadable within the Xurrent platform. Additionally, customers can even rotate keys according to their internal policies.

**BONUS: All of the above**_without negatively impacting user experience or the lightning-fast performance customers have come to expect from Xurrent._
