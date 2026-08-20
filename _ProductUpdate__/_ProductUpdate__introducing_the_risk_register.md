---
title: "Introducing the Risk Register"
date: "March 4, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-the-risk-register"
slug: "introducing-the-risk-register"
---

# Introducing the Risk Register

As part of their compliance efforts, organizations practice risk management.  They do this to ensure that they identify potential risks in advance, analyze these risks and take precautionary steps to eliminate them, or at least minimize their likelihood and/or the impact they could have on the organization.

To ensure full support for governance, risk management and compliance ([GRC](https://en.wikipedia.org/wiki/Governance,_risk_management,_and_compliance)), organizations can now maintain their risk register in Xurrent.  Why in Xurrent? Well, there are several reasons.

First, organizations are discovering that Xurrent’s request templates, change templates and especially the recurring change templates, are ideal for making sure that they stay compliant.  Thanks to Xurrent’s audit capabilities, they can also easily proof this to auditors.  Having the risk register as an integral part of Xurrent keeps everything in a single secure and audited environment.

Another obvious reason is that project managers need to be able to manage the risks that have been identified for their projects.  Being able to relate these risks to the projects that may become affected by them, gives project managers a single place where they can manage their projects, as well as the associated risks.

A final reason for adding risk management functionality to Xurrent is that some risks may originate from vendors or managed service providers (MSPs) that the organization relies on.  And a service that the organization is using can also pose a threat, for example because its security measures are deemed insufficient to adequately protect the data that is captured by the service.

Having the ability to not only register risks, but also to look up a project, service or organization to see the related risks, provides a significant benefit for project and vendor management, as well as the [SIAM](https://www.xurrent.com/solutions/it-service-management) service integrator function.

#### Activating Risk Management

The Risk Management functionality can be activated in a Xurrent account by its account owner.  The account owner can do this in the ‘Account Settings’ section of the Settings console by simply checking the Risk management box.

As soon as risk management is activated, the section ‘Risk Severities’ gets added to the Settings console.  This section already contains four risk severities, which are the options for the Severity field of the Risk form.  These four default risk severities can be adjusted as needed.

Account administrators can adjust these options for the Severity field of the Risk form as needed.  They can also add more severity options, or disable them.  Drag-and-drop is enabled in the ‘Risk Severities’ section of the Settings console so that the severities can quickly be placed in a logical order.

In addition to the risk severities, Xurrent also adds a [UI extension](https://www.xurrent.com/blog/advanced-ui-extension-examples) when risk management is activated.  This UI extension adds the ‘Risk Assessment’ section to the risk form.

The JavaScript of this UI extension ensures that the value in the Severity field is automatically updated to the correct value when an option is selected in the in Likelihood and Impact fields.  This UI extension is relatively advanced, so having this example should make it easier to adjust its JavaScript so that it matches the logic of the organization’s risk assessment matrix.

For organizations that do not have such a matrix yet, this default UI extension, in combination with the default options for the Severity field, provide a good starting point.

#### Risk Registration

With risk management activated, all specialists will see the ‘Risks’ option when they click on the icon of the Records console.

That is where specialists can go after they have identified a new risk to register it. Alternatively, specialists can add a new risk to their organization’s risk register by clicking on the ‘Relate to New Risk…’ option that becomes available in the Actions menu when a project, service or organization has been placed in View mode.

Every specialist is allowed to add risks to their organization’s risk register.  This helps to ensure that all risks get captured as soon as they have been identified.

The form for registering a new risk will feel comfortable for people who have already been using Xurrent for a while.

After a risk has been registered, a compliance officer or project manager can take over to review and adjust the assessment, and then decide on the actions that should be taken to eliminate or minimize the risk.

When someone takes over the responsibility for a risk by selecting his or her person record in the Manager field, the previous manager is automatically notified by Xurrent.  Until someone is the manager of a risk, this person will not be able to do anything other than update the risk’s manager and add notes.

Xurrent also sends a notification to the manager for each note that is added by someone other than the risk’s manager.  These notifications help to ensure that specialists cannot take over or update someone else’s risks without the manager getting notified.  And naturally any update causes an audit entry to be added to the risk’s audit trail.

When the manager of a risk decides that one or more actions need to be taken to mitigate the risk, these actions can be requested by submitting new requests in Xurrent.  These requests can then be handled through the normal processes where problem, change, project and/or knowledge management may need to get involved.

[References](https://www.xurrent.com/blog/reference-other-records) to these requests, problems, changes, etc.  can be included in the notes of risks so that it is easy to get a chronological overview of the steps that have been taken to protect the organization from each risk.

