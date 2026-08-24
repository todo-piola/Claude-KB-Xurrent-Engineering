---
title: "Set Time Zone with OpenID Connect and JIT"
date: "February 17, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/set-time-zone-with-openid-connect-and-jit"
slug: "set-time-zone-with-openid-connect-and-jit"
---

# Set Time Zone with OpenID Connect and JIT

When [Just-in-Time (JIT) provisioning is activated in an OpenID Connect single sign-on configuration](https://www.xurrent.com/product-updates/give-anyone-access-to-self-service), a new person record is automatically generated when someone who is not yet registered in Xurrent is trying to access Xurrent Self Service.  In such cases, Xurrent’s JIT functionality asks the identity provider to return several claims so that it can add the following information to the new person record:

- **Name** — uses the `name` claim, or if not provided, the `given_name`,  `middle_name` and `family_name` claims
- **Email address** — uses the `email` claim
- **Picture** — uses the `picture` claim
- **Language preference** — uses the `locale` claim
- **Time zone** — uses the `zoneinfo` claim

This last piece of information is new.  It ensures that people see date and time information (such as the resolution target of requests) in their time zone, rather than the default time zone of the account in which their person record is registered.

Unfortunately, the most commonly used identity providers (like Microsoft, Google and Apple) do not yet support the `zoneinfo` claim by default.  Once they start to do this, though, Xurrent will automatically pick it up and use it to set the time zone preference in the new person records that the JIT provisioning functionality generates.

