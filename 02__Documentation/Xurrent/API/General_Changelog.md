# Change Log

## August 1, 2026

- Updated: [KnowledgeArticleFilter](https://developer.xurrent.com/graphql/input_object/knowledgearticlefilter/#timesviewed): added the `timesViewed` field.
- Updated: [Knowledge Articles](../../knowledge_articles.html#times_viewed): added the `times_viewed` field.

## July 25, 2026

- Updated: [ConfigurationItem](https://developer.xurrent.com/graphql/object/configurationitem/#locationhint): added the `locationHint` field.
- Updated: [DiscoveredCiInput](https://developer.xurrent.com/graphql/input_object/discoveredciinput/#locationhint): added the `locationHint` field.
- Updated: [Configuration Items](../../configuration_items/index.html#location_hint): added the `location_hint` field.

## July 20, 2026

- Updated: [Configuration Items](../../configuration_items/index.html#fields): documented the existing `end_of_support_date` and `last_seen_at` fields.

## July 16, 2026

- New: [Workflows - Tags](../../workflows/tags/index.html), [Problems - Tags](../../problems/tags/index.html), [Projects - Tags](../../projects/tags/index.html), [Tasks - Tags](../../tasks/tags/index.html), and [Project Tasks - Tags](../../project_tasks/tags/index.html): tags can now be listed, added and removed.
- Updated: [Workflow](https://developer.xurrent.com/graphql/object/workflow/#tags), [Problem](https://developer.xurrent.com/graphql/object/problem/#tags), [Project](https://developer.xurrent.com/graphql/object/project/#tags), [Task](https://developer.xurrent.com/graphql/object/task/#tags), and [ProjectTask](https://developer.xurrent.com/graphql/object/projecttask/#tags): added the `tags` connection.
- Updated: [WorkflowCreateInput](https://developer.xurrent.com/graphql/input_object/workflowcreateinput/#newtags), [ProblemCreateInput](https://developer.xurrent.com/graphql/input_object/problemcreateinput/#newtags), [ProjectCreateInput](https://developer.xurrent.com/graphql/input_object/projectcreateinput/#newtags), [TaskCreateInput](https://developer.xurrent.com/graphql/input_object/taskcreateinput/#newtags), and [ProjectTaskCreateInput](https://developer.xurrent.com/graphql/input_object/projecttaskcreateinput/#newtags): added the `newTags` field.
- Updated: [WorkflowUpdateInput](https://developer.xurrent.com/graphql/input_object/workflowupdateinput/#newtags), [ProblemUpdateInput](https://developer.xurrent.com/graphql/input_object/problemupdateinput/#newtags), [ProjectUpdateInput](https://developer.xurrent.com/graphql/input_object/projectupdateinput/#newtags), [TaskUpdateInput](https://developer.xurrent.com/graphql/input_object/taskupdateinput/#newtags), and [ProjectTaskUpdateInput](https://developer.xurrent.com/graphql/input_object/projecttaskupdateinput/#newtags): added the `newTags` and `tagsToDelete` fields.

## July 4, 2026

- New: [ChildSourceRefInput](https://developer.xurrent.com/graphql/input_object/childsourcerefinput/).
- New: [CiRelationSourceKeyInput](https://developer.xurrent.com/graphql/input_object/cirelationsourcekeyinput/).
- Updated: [CiRelationInput](https://developer.xurrent.com/graphql/input_object/cirelationinput/#configurationitemsource): added the `configurationItemSource` and `configurationItemSourceID` fields.
- Updated: [ConfigurationItemUpdateInput](https://developer.xurrent.com/graphql/input_object/configurationitemupdateinput/#cirelationstodeletebysource): added the `ciRelationsToDeleteBySource` field.
- Updated: [DiscoveredCiRelationInput](https://developer.xurrent.com/graphql/input_object/discoveredcirelationinput/#childsourcerefs): added the `childSourceRefs` field.
- Updated: [RequestTemplate](https://developer.xurrent.com/graphql/object/requesttemplate/#translatesubject): added the `translateSubject` field.
- Updated: [RequestTemplateCreateInput](https://developer.xurrent.com/graphql/input_object/requesttemplatecreateinput/#translatesubject): added the `translateSubject` field.
- Updated: [RequestTemplateUpdateInput](https://developer.xurrent.com/graphql/input_object/requesttemplateupdateinput/#translatesubject): added the `translateSubject` field.
- Updated: [Currency](https://developer.xurrent.com/graphql/scalar/currency/): added the Serbian Dinar (`rsd`) currency.
- Updated: [Request Templates](../../request_templates.html#translate_subject): added the `translate_subject` field.

## June 13, 2026

- Updated: [ConfigurationItemCreatePayload](https://developer.xurrent.com/graphql/object/configurationitemcreatepayload/#pendingcireconciliation): added the `pendingCiReconciliation` field.
- Updated: [ConfigurationItemUpdatePayload](https://developer.xurrent.com/graphql/object/configurationitemupdatepayload/#pendingcireconciliation): added the `pendingCiReconciliation` field.
- Updated: [DiscoveredConfigurationItemsPayload](https://developer.xurrent.com/graphql/object/discoveredconfigurationitemspayload/#pendingcireconciliationcount): added the `pendingCiReconciliationCount` field.
- Updated: [ShopArticleFilter](https://developer.xurrent.com/graphql/input_object/shoparticlefilter/#isbundle): added the `isBundle` field.
- Updated: [Shop Articles](../../shop_articles/index.html#is_bundle): added the `is_bundle` field.

## June 6, 2026

- Updated: [ProductCategory](https://developer.xurrent.com/graphql/object/productcategory/#reviewendofsupportdays): added the `reviewEndOfSupportDays`, `reviewInUseSinceDays`, `reviewLastSeenDays`, `reviewLicenseExpiryDays`, and `reviewWarrantyExpiryDays` fields.
- Updated: [ProductCategoryCreateInput](https://developer.xurrent.com/graphql/input_object/productcategorycreateinput/#reviewendofsupportdays): added the `reviewEndOfSupportDays`, `reviewInUseSinceDays`, `reviewLastSeenDays`, `reviewLicenseExpiryDays`, and `reviewWarrantyExpiryDays` fields.
- Updated: [ProductCategoryUpdateInput](https://developer.xurrent.com/graphql/input_object/productcategoryupdateinput/#reviewendofsupportdays): added the `reviewEndOfSupportDays`, `reviewInUseSinceDays`, `reviewLastSeenDays`, `reviewLicenseExpiryDays`, and `reviewWarrantyExpiryDays` fields.
- Updated: [Product Categories](../../product_categories/index.html#review_end_of_support_days): added the `review_end_of_support_days`, `review_in_use_since_days`, `review_last_seen_days`, `review_license_expiry_days`, and `review_warranty_expiry_days` fields.

## May 23, 2026

- Updated: [GoldenSetItem](https://developer.xurrent.com/graphql/object/goldensetitem/#runas) and [SeraAiStudio](https://developer.xurrent.com/graphql/object/seraaistudio/#runas): replaced the `person` field with `runAs`.

## May 16, 2026

- Updated: [Note Reactions](../../notes/note_reactions/index.html): corrected `account`.`id` field from integer (10) to sitename (“widget”).
- Removed: VirtualAgentDesign — replaced by [SeraAiStudio](https://developer.xurrent.com/graphql/object/seraaistudio/).
- New: [SeraAiStudio](https://developer.xurrent.com/graphql/object/seraaistudio/).
- New: [GoldenSetItem](https://developer.xurrent.com/graphql/object/goldensetitem/).
- Updated: [Account](https://developer.xurrent.com/graphql/object/account/#seraaistudio): added the `seraAiStudio` field.
- Updated: [Account](https://developer.xurrent.com/graphql/object/account/#virtualagentdesign): removed the `virtualAgentDesign` field.
- Updated: [KnowledgeArticle](https://developer.xurrent.com/graphql/object/knowledgearticle/): now implements the `HasGoldenSetExpectedHits` interface.
- Updated: [RequestTemplate](https://developer.xurrent.com/graphql/object/requesttemplate/): now implements the `HasGoldenSetExpectedHits` interface.

## May 9, 2026

- Updated: [Requests](../../requests.html#closure_code): the `closure_code` field is now documented as an enum.
- Updated: [Request Templates](../../request_templates.html#action_type): added the `action_type` field.
- Updated: [Request Templates](../../request_templates.html#description): added the `description` field.

## May 5, 2026

- Documented: [Data Types](../data_types.html#id): the `:id` URL path parameter accepts either the numeric `id` or the `nodeID`.

## May 2, 2026

- Updated: [VirtualAgentDesign](https://developer.xurrent.com/graphql/object/virtualagentdesign/#agentinstructionsdraft): added the `agentInstructionsDraft` field.
- Updated: [VirtualAgentDesignUpdateInput](https://developer.xurrent.com/graphql/input_object/virtualagentdesignupdateinput/#agentinstructionsdraft): added the `agentInstructionsDraft` field.
- Updated: [VirtualAgentDesignUpdateInput](https://developer.xurrent.com/graphql/input_object/virtualagentdesignupdateinput/#agentinstructions): removed the `agentInstructions` field.

## April 25, 2026

- New: [VirtualAgentDesign](https://developer.xurrent.com/graphql/object/virtualagentdesign/).
- New: [VirtualAgentDesignUpdateInput](https://developer.xurrent.com/graphql/input_object/virtualagentdesignupdateinput/).
- Updated: [Account](https://developer.xurrent.com/graphql/object/account/#virtualagentdesign): added the `virtualAgentDesign` field.
- Updated: [RequestCreateInput](https://developer.xurrent.com/graphql/input_object/requestcreateinput/#organizationid): added the `organizationId` field.
- Updated: [RequestUpdateInput](https://developer.xurrent.com/graphql/input_object/requestupdateinput/#organizationid): added the `organizationId` field.
- New: Improved [.NET REST SDK for Xurrent](../libraries.html) has been released, and is now also available as a [NuGet package](https://www.nuget.org/packages/Works4me.Xurrent.Rest).

## April 18, 2026

- Updated: [TimeEntryView](https://developer.xurrent.com/graphql/enum/timeentryview/): added the `all_for_data_sync` value.
- Updated: [App Offerings](../../app_offerings/index.html): added the `openid_connect_discovery` field.
- Updated: [Webhooks](../../webhooks.html): added the `openid_connect_discovery` field.
- Updated: [Service Offering RFC Type Rates](../../service_offerings/rfc_type_rates/index.html): `charge_type` is now optional.

## April 11, 2026

- New: [RequestTemplateActionTypeFilter](https://developer.xurrent.com/graphql/input_object/requesttemplateactiontypefilter/).
- Updated: [RequestTemplate](https://developer.xurrent.com/graphql/object/requesttemplate/#actiontype): added the `actionType` and `description` fields.
- Updated: [RequestTemplateCreateInput](https://developer.xurrent.com/graphql/input_object/requesttemplatecreateinput/#actiontype): added the `actionType` and `description` fields.
- Updated: [RequestTemplateUpdateInput](https://developer.xurrent.com/graphql/input_object/requesttemplateupdateinput/#actiontype): added the `actionType` and `description` fields.
- Updated: [RequestTemplateFilter](https://developer.xurrent.com/graphql/input_object/requesttemplatefilter/#actiontype): added the `actionType` filter.
- Updated: [Tasks](../../tasks.html): added the `copy_note_to_request` and `copy_note_to_workflow` fields.

## April 4, 2026

- Added: [Task](https://developer.xurrent.com/graphql/object/task/): added the `copyNoteToRequest` and `copyNoteToWorkflow` fields. Also added to the [TaskCreateInput](https://developer.xurrent.com/graphql/input_object/taskcreateinput/) and [TaskUpdateInput](https://developer.xurrent.com/graphql/input_object/taskupdateinput/) mutations.
- Updated: [TaskTemplate](https://developer.xurrent.com/graphql/object/tasktemplate/#translations): added the `translations` field.

## March 25, 2026

- Updated: [Webhooks](../../webhooks.html#automatic-key-discovery): the public key for payloads signed using a policy can now be discovered automatically (via OpenID Connect Discovery).
- Updated: [Webhook](https://developer.xurrent.com/graphql/object/webhook/#openidconnectdiscovery): added the `openidConnectDiscovery` field.
- Updated: [AppOffering](https://developer.xurrent.com/graphql/object/appoffering/#openidconnectdiscovery): added the `openidConnectDiscovery` field.

## March 16, 2026

- New: [Token Exchange Grant](../../oauth/token_exchange_grant/index.html): added documentation for the RFC 8693 token exchange grant type, allowing external systems to exchange a third-party JWT for a short-lived Xurrent access token.

## March 14, 2026

- New: [RfcTypeActivityID](https://developer.xurrent.com/graphql/object/rfctypeactivityid/) and [Service Level Agreements - RFC Type Activity IDs](../../service_level_agreements/rfc_type_activityIDs/index.html).
- New: [RfcTypeRate](https://developer.xurrent.com/graphql/object/rfctyperate/) and [Service Offerings - RFC Type Rates](../../service_offerings/rfc_type_rates/index.html).
- New: [Service Offerings - RFC Type Activity Rates Import](../../import/service_offering_rfc_type_activity_rates/index.html).
- New: [Service Level Agreements - RFC Type Activities Import](../../import/slas_financial_details_rfc_type_activities/index.html).
- New: [Templated Tokens](../../oauth/templated_tokens/index.html): added support for pre-filling token and OAuth application forms via URL parameters.
- Updated: [ServiceLevelAgreement](https://developer.xurrent.com/graphql/object/servicelevelagreement/#rfctypeactivityids): added the `rfcTypeActivityIDs` field.
- Updated: [ServiceOffering](https://developer.xurrent.com/graphql/object/serviceoffering/#rfctyperates): added the `rfcTypeRates` field.
- Updated: [RFC Type](../../rfc_types.html): removed the `description` field.
- Fixed: [ServiceLevelAgreementUpdateInput](https://developer.xurrent.com/graphql/input_object/servicelevelagreementupdateinput/#standardservicerequestactivityidstodelete): corrected the description of the `standardServiceRequestActivityIDsToDelete` field.

## March 5, 2026

- New: [RFC Type](../../rfc_types.html).
- New: [RFC Type Import](../../import/rfc_types/index.html).
- Updated: [Request Template](../../request_templates.html): added the `rfc_type` field.
- Updated: [Request](../../requests.html): added the `rfc_type` field.

## February 9, 2026

- Added: [Audit Entries](../../audit_entries.html): added `info` action value and `user` field.
- Added: [Service Level Agreements - Effort Class Rate IDs](../../service_level_agreements/effort_class_rateIDs/index.html): added Remove All endpoint and corrected POST response to `201`.
- Added: [Service Level Agreements - Standard Service Request Activity IDs](../../service_level_agreements/standard_service_request_activityIDs/index.html): added Remove All endpoint and corrected POST response to `201`.
- Added: [Service Offerings - Effort Class Rates](../../service_offerings/effort_class_rates/index.html): added Remove All endpoint and corrected POST response to `201`.
- Updated: [Account - Billable Users](../../account/billable_users/index.html): corrected `name` and `organization` fields from Required to Readonly.
- Updated: [PDF Designs](../../pdf_designs/index.html): corrected `category` field from Readonly to Required.
- Updated: [Project Tasks](../../project_tasks.html): corrected `assigned_at` and `finished_at` fields from Optional to Readonly.
- Updated: [Project Templates - Phases](../../project_templates/phases/index.html): corrected POST response from `200` to `201`.
- Updated: [Projects - Phases](../../projects/phases.html): corrected POST response from `200` to `201`.
- Updated: [Shop Order Lines](../../shop_order_lines/index.html): documented status-dependent writable fields for PATCH.
- Updated: [Timesheet Settings](../../timesheet_settings/index.html): added allowed values for `time_increment` field.
- Updated: [Timesheets](../../timesheets/index.html): corrected `workdays` field type from integer to decimal.
- Updated: Corrected POST response from `200` to `201` for sub-resource creation endpoints: [Agile Board Columns](../../agile_boards/columns.html), [Broadcast Translations](../../broadcasts/translations/index.html), [Project Task Templates](../../project_templates/project_task_templates/index.html), [Request Watches](../../requests/watches.html), [Survey Questions](../../surveys/survey_questions/index.html), [Task Approvals](../../tasks/approvals.html), [Waiting for Customer Rules](../../waiting_for_customer_follow_ups/waiting_for_customer_rules/index.html), [Workflow Phases](../../workflows/phases.html), [Workflow Template Phases](../../workflow_templates/phases.html).
- Updated: [Note Reactions](../../notes/note_reactions/index.html): corrected response structure and removed top-level `account` field.
- Updated: [Permissions](../../people/permissions.html): corrected `roles` field type from array of string to array of enum.
- Updated: [Me](https://developer.xurrent.com/v1/me/): removed `permissions` from the example response as it is not returned by the `/me` endpoint.

## February 5, 2026

- New: [Shop Articles - Service Offerings](../../shop_articles/service_offerings/index.html) added the ability to access the service offerings of a shop article.

## January 29, 2026

- Updated: [Languages](https://developer.xurrent.com/graphql/scalar/language) added German/French/Italian Swiss language codes.

## January 13, 2026

- Added: [Agile Boards - Customer Representative SLAs](../../agile_boards/customer_representative_slas/index.html): added Remove All endpoint.
- Added: [App Instances](../../app_instances/index.html): added POST and PATCH endpoints.
- Added: [App Offering Automation Rules](../../app_offering_automation_rules/index.html): added `/for_problems` predefined filter and `Problem` rulable type.
- Added: [Automation Rules](../../automation_rules.html): added DELETE endpoint.
- Added: [Broadcasts - Teams](../../broadcasts/teams/index.html): added Remove All endpoint.
- Added: [Calendar Hours](../../calendars/calendar_hours/index.html): added GET single endpoint.
- Added: [First Line Support Agreements](../../first_line_support_agreements/audit/index.html): added audit entries endpoint.
- Added: [Notes](../../notes.html): added the `suppress_note_added_notifications` field.
- Added: [Service Level Agreements](../../service_level_agreements.html): added `coverage_groups` enum value to `coverage` field.
- Added: [Service Level Agreements](../../service_level_agreements/coverage_groups/index.html): added Coverage Groups endpoint.
- Added: [Shop Article Categories](../../shop_article_categories/index.html): added the `attachments`, `full_description_attachments` and `parent` fields.
- Added: [Shop Articles](../../shop_articles/index.html): added the `attachments` field.
- Added: [SLA Coverage Groups](../../sla_coverage_groups/slas/index.html): added Service Level Agreements endpoint.
- Added: [SLA Notification Rules](../../sla_notification_schemes/sla_notification_rules/index.html): added GET single and PATCH endpoints.
- Added: [Survey Answers](../../survey_responses/survey_answers/index.html): added DELETE endpoint.
- Added: [Time Entries](../../time_entries.html): added the `note_nodeID` field.
- Added: [UI Extension Versions](../../ui_extensions/versions.html): added the `dark_mode_safe`, `form_definition_react`, and `use_designer` fields.
- Added: [UI Extensions](../../ui_extensions.html): added the `dark_mode_safe`, `form_definition_json`, `hide_note`, and `show_on_complete` fields.
- Added: [Waiting for Customer Follow Ups](../../waiting_for_customer_follow_ups/index.html): added the `auto_complete` field and PATCH endpoint.
- Added: [Webhook Policies](../../webhook_policies.html): added DELETE endpoint.
- Added: [Webhooks](../../webhooks/events.html): added the `created_at` field.
- Fixed: [App Offerings](../../app_offerings/index.html): the `attachments` field now works with the `?fields=` parameter.
- Fixed: [Configuration Items](../../configuration_items/index.html): removed incorrect default values from the `name` and `remarks` fields.
- Fixed: [Custom Collections](../../custom_collections/index.html): the `attachments` field now works with the `?fields=` parameter.
- Fixed: [Organizations - Contacts](../../organizations/contacts/index.html): corrected URL parameter from `:id` to `:contact_id`.
- Fixed: [Service Offerings](../../service_offerings/index.html): corrected `availability` type from float to decimal.
- Fixed: [Shop Articles](../../shop_articles/index.html): corrected `max_quantity` type from decimal to integer.

## January 9, 2026

- Updated: [Reservation](https://developer.xurrent.com/graphql/object/reservation/#lifecyclestate): added the `lifeCycleState` field.
- Updated: [Sprint](https://developer.xurrent.com/graphql/object/sprint/#name): added the `name` field.
- Updated: [Workflow](https://developer.xurrent.com/graphql/object/workflow/#preventrequestcompletion): added the `preventRequestCompletion` field.
- Updated: [WorkflowTemplate](https://developer.xurrent.com/graphql/object/workflowtemplate/#preventrequestcompletion): added the `preventRequestCompletion` field.

## December 5, 2025

- Updated: [TaskTemplate](https://developer.xurrent.com/graphql/object/tasktemplate/#copynotestorequest): added the `copyNotesToRequest` field.

## November 25, 2025

- Updated: [RequestFilter](https://developer.xurrent.com/graphql/input_object/requestfilter/): added filter `workflowPhase`.
- Updated: [TimeEntryFilter](https://developer.xurrent.com/graphql/input_object/timeentryfilter/): added filter `request`.
- Updated: [TimeZone](https://developer.xurrent.com/graphql/scalar/timezone/): added `Nigeria` timezone.

## November 8, 2025

- Updated: [JIT Provisioning](../../jit_provisioning/openid_connect.html): added support for `organization`, `site` and `manager` to OpenID Connect.

## October 30, 2025

- Updated: [Agile Board](https://developer.xurrent.com/graphql/object/agileboard/): added the `requestTemplate` field.
- Updated: [Agile Board](https://developer.xurrent.com/graphql/object/agileboard/): added the `serviceInstance` field.
- Updated: [Product Backlog](https://developer.xurrent.com/graphql/object/productbacklog/): added the `requestTemplate` field.
- Updated: [Product Backlog](https://developer.xurrent.com/graphql/object/productbacklog/): added the `serviceInstance` field.

## October 2, 2025

- Updated: [UI Extension](https://developer.xurrent.com/graphql/object/uiextension/): added the `darkModeSafe` field.

## September 19, 2025

- Updated: Field `pictureUri` arguments of GraphQL mutations (e.g. the [pictureUri to update a person’s avatar](https://developer.xurrent.com/graphql/mutation/personupdate/#pictureuri)) now also accept [‘data URLs’](https://developer.mozilla.org/en-US/docs/Web/URI/Reference/Schemes/data). The same goes for the `picture_uri` field when creating and updating records via the REST API. These images should be less than 2MB in size. In general, we support images in either JPG, GIF, WEBP, PNG or SVG format. Specifically for people we **do not** support SVGs.

## September 5, 2025

- Updated: Field `ownerID` is required in the [create notes](https://developer.xurrent.com/graphql/mutation/notecreate/) GraphQL API.

## August 22, 2025

- Changed: [Closure Codes](https://developer.xurrent.com/graphql/object/closurecode/): added `translations` connection.

## August 1, 2025

- Changed: The domain of Short URLs will change from [4me.io](https://4me.io) to [io.xurrent.com](https://io.xurrent.com).
 - This change is backwards compatible, which means that previously circulated URLs that use `4me.io` will continue to work.
 - In other Xurrent regions other than EU, the URL will contain a region code. For example, `uk.4me.io` will change to `io.uk.xurrent.com`, etc.

## July 9, 2025

- Added: [Closure Codes](../../closure_codes/index.html) to the REST API.
- Added: [Closure Codes](https://developer.xurrent.com/graphql/object/closurecode/) to the GraphQL API.
- Added: Closure Codes support to the [Import API](../../import/closure_codes/index.html) and [Export API](../../export.html).
- Updated: [Requests](../../requests.html): added `closure_code`.
- Updated: [Request](https://developer.xurrent.com/graphql/object/request/): added `closureCodeId`.
- Updated: [Account](https://developer.xurrent.com/graphql/object/account/): added `design`.
- Updated: [Account Design](https://developer.xurrent.com/graphql/object/accountdesign/): added `logoUri`.
- Fixed: It was possible for [Oauth applications with a client credentials grant](../../oauth/client_credentials_grant.html) to directly construct a valid bearer token to perform Xurrent API requests, instead of performing an access token request first. This improper use of client credentials is no longer possible.

## June 20, 2025

- Added ability to delete out of office periods to the [GraphQL API](https://developer.xurrent.com/graphql/mutation/outofofficeperioddelete/)
 and to the [REST API](../../out_of_office_periods.html#remove-an-out-of-office-period).
- Added: [People - Out of Office Periods](../../people/out_of_office_periods/index.html) to the REST API.

## June 13, 2025

- Updated: [ProblemFilter](https://developer.xurrent.com/graphql/input_object/problemfilter/): added filter `serviceInstance`.

## April 25, 2025

- Updated: [AppOfferingScope](https://developer.xurrent.com/graphql/object/appofferingscope/): removed field `conditions` (it was never filled).
- Updated: [TimesheetSetting](https://developer.xurrent.com/graphql/object/timesheetsetting/#requiretimeentrydescription): added field `requireTimeEntryDescription` to indicate all time entries must have a description. For this reason all mutations that can create or update a record and create a time entry have been given a new field too `timeEntryDescription`, see for instance [problemCreate Mutation](https://developer.xurrent.com/graphql/mutation/problemcreate/#timeentrydescription).

## April 18, 2025

- Updated: [Webhook](https://developer.xurrent.com/graphql/object/webhook/): added field `appOfferingReferences`.
- Updated: [WebhookCreate Mutation](https://developer.xurrent.com/graphql/mutation/webhookcreate/): added `appOfferingReferences`.
- Updated: [WebhookUpdate Mutation](https://developer.xurrent.com/graphql/mutation/webhookupdate/): added `appOfferingReferences`.
- Fixed: [Standard Service Request Activity ID](https://developer.xurrent.com/graphql/object/standardservicerequestactivityid/):
 the non-existing fields `createdAt` and `updatedAt` have been removed.

## January 2, 2025

- Updated: [Account](https://developer.xurrent.com/graphql/object/account/): added field `directoryAccount`.
- Updated: [RequestFilter](https://developer.xurrent.com/graphql/input_object/requestfilter/): added filter `customerTargetAt`.

## December 5, 2024

- Renamed all occurrences of 4me.com to xurrent.com

## November 30, 2024

- Updated: [ProductCategoryFilter](https://developer.xurrent.com/graphql/input_object/productcategoryfilter/): added new filter options.

## November 23, 2024

- New: [UI Extension Javascript API](../../ui_extensions/js_api.html): added `status`, `impact` to the list of Request fields that can be interacted with in Self Service.

## November 16, 2024

- New: [UI Extension Javascript API](../../ui_extensions/js_api.html): added `status` to the list of Knowledge Article fields that can be interacted with.
- New: [UI Extension Javascript API](../../ui_extensions/js_api.html): added `ram_amount` to the list of CI fields that can be interacted with.
- Updated: [Account](https://developer.xurrent.com/graphql/object/account/): added field `directory`.

## November 2, 2024

- Removed: [Service Offering](https://developer.xurrent.com/graphql/object/serviceoffering/): the deprecated fields
 `slaNotificationSchemeLow`, `slaNotificationSchemeMedium`, `slaNotificationSchemeHigh` and `slaNotificationSchemeTop`
 are removed.
- Removed: [Standard Service Request](https://developer.xurrent.com/graphql/object/standardservicerequest/): the deprecated field
 `slaNotificationScheme` is now removed.
- Removed: Similar deprecations for the REST API and Bulk API (Import and Export).
- Removed: [EffortClassRateID](https://developer.xurrent.com/graphql/object/effortclassrateid/): the fields `created_at` and
 `updated_at` are removed.
- Updated: [RecurrenceTemplate](https://developer.xurrent.com/graphql/object/recurrencetemplate/): changed type of field `dayOfWeekDay` to be a single value instead of an array.

## October 26, 2024

- Updated: Added option to filter on `template` to [AffectedSlaFilter](https://developer.xurrent.com/graphql/input_object/affectedslafilter/).

## October 12, 2024

- Updated: [Request](https://developer.xurrent.com/graphql/object/request/): added field `summary`
- Updated: All response header fields (e.g. `Content-Type`, `X-Pagination-Per-Page`) must be handled case-insensitive.
 This has always been mandated by the HTTP standard, but from this date, and as mandated by the HTTP/2 standard,
 Xurrent will start using lowercase variants (e.g. `content-type`, `x-pagination-per-page`).

 Most frameworks handle case-insensitivity for HTTP headers automatically, so this change won’t affect you
 if you’re using one of the following examples:

 - Ruby SDK: `responseMessage.Headers["X-Pagination-Per-Page"]`
 - JavaScript: `XMLHttpRequest.getResponseHeader("X-Pagination-Per-Page")`
 - .NET: `System.Net.Http.Headers.HttpResponseHeaders.GetValues()` or `System.Net.Http.Headers.HttpResponseHeaders.TryGetValues()`

 In .NET, both the REST and GraphQL SDKs utilize `System.Net.Http.Headers.HttpResponseHeaders` and
 `HttpWebResponse.Headers`, ensuring they are not impacted by any changes related to header case-sensitivity.

 In the REST API and GraphQL API the following response header fields are downcased:

 - X-Pagination-Current-Page –> x-pagination-current-page
 - X-Pagination-Per-Page –> x-pagination-per-page
 - X-Pagination-Total-Entries –> x-pagination-total-entries
 - X-Pagination-Total-Pages –> x-pagination-total-pages
 - X-Pagination-Throttled –> x-pagination-throttled
 - X-Pagination-Next-Page –> x-pagination-next-page
 - X-Pagination-Last-Page –> x-pagination-last-page
 - Link –> link

## October 5, 2024

- Updated: [Service Offering](https://developer.xurrent.com/graphql/object/serviceoffering/): added fields
 `responseTargetNotificationSchemeLow`, `responseTargetNotificationSchemeMedium`, `responseTargetNotificationSchemeHigh` and `responseTargetNotificationSchemeTop`.
- Updated: [Service Offering](https://developer.xurrent.com/graphql/object/serviceoffering/): added fields
 `resolutionTargetNotificationSchemeLow`, `resolutionTargetNotificationSchemeMedium`, `resolutionTargetNotificationSchemeHigh` and `resolutionTargetNotificationSchemeTop`.
- Updated: [Standard Service Request](https://developer.xurrent.com/graphql/object/standardservicerequest/): added field `responseTargetNotificationScheme`.
- Updated: [Standard Service Request](https://developer.xurrent.com/graphql/object/standardservicerequest/): added field `resolutionTargetNotificationScheme`.
- **Deprecated**:
 - [Service Offering](https://developer.xurrent.com/graphql/object/serviceoffering/): the fields
 `slaNotificationSchemeLow`, `slaNotificationSchemeMedium`, `slaNotificationSchemeHigh` and `slaNotificationSchemeTop` are now deprecated.
 Use the fields `resolutionTargetNotificationSchemeLow`, `resolutionTargetNotificationSchemeMedium`, `resolutionTargetNotificationSchemeHigh` and `resolutionTargetNotificationSchemeTop` instead.
 - [Standard Service Request](https://developer.xurrent.com/graphql/object/standardservicerequest/): the field
 `slaNotificationScheme` is now deprecated. Use the field `resolutionTargetNotificationScheme` instead.
 - There are similar deprecations for the REST API and Bulk API (Import and Export).
 - The deprecated fields will be removed in QA on **November 2, 2024**, and in Production on **November 9, 2024**.

## September 21, 2024

- Updated: [FirstLineSupportAgreement](https://developer.xurrent.com/graphql/object/firstlinesupportagreement): added `majorIncidentManagers` field.
- Updated: [Account](https://developer.xurrent.com/graphql/object/account/): added `url` field.

## September 14, 2024

- Updated: [Request](https://developer.xurrent.com/graphql/object/request/): added `feedbackOnKnowledgeArticle` field.
- Added: [First Line Support Agreements - Major Incident Managers API](../../first_line_support_agreements/major_incident_managers.html)

## September 5, 2024

- 4me is now known as [Xurrent](https://www.xurrent.com)! The developer documentation has been updated to reflect this change.
- Updated: All GraphQL mutations for records with a rich text `information` field allow `informationAttachments` as input arguments.

## August 31, 2024

- Changed: REST API and GraphQL API response header fields for `x-costlimit-*`, `x-ratelimit-*` and `retry-after` are downcased.

## August 17, 2024

- Updated: [ProjectTaskTemplate](https://developer.xurrent.com/graphql/object/projecttasktemplate/): added `agileBoard` and `agileBoardColumn` fields.
- Updated: [ProjectTaskTemplateCreate Mutation](https://developer.xurrent.com/graphql/mutation/projecttasktemplatecreate/): added `agileBoardColumnId` and `agileBoardId`
- Updated: [ProjectTaskTemplateUpdate Mutation](https://developer.xurrent.com/graphql/mutation/projecttasktemplateupdate/): added `agileBoardColumnId` and `agileBoardId`

## July 20, 2024

- Updated: [DiscoveredCiInput](https://developer.xurrent.com/graphql/input_object/discoveredciinput/): added `assetID` field.
- Updated: [UiExtensionVersion](https://developer.xurrent.com/graphql/object/uiextensionversion/): added `formDefinition` field.

## July 13, 2024

- Updated: [ConfigurationItem](https://developer.xurrent.com/graphql/object/configurationitem/): changed the data type of the `ramAmount` field to decimal.
- Updated: [DiscoveredCiInput](https://developer.xurrent.com/graphql/input_object/discoveredciinput/): changed the data type of the `ramAmount` field to decimal.
- Updated: [Organization](https://developer.xurrent.com/graphql/object/organization/): added the `endUserPrivacy` field.

## June 22, 2024

- Added: `pictureUri` argument to GraphQL mutations for App Offerings, Custom Collections and Service Instances to allow their avatar to be set.
- Added: `effortClassId` argument to GraphQL mutations for Out of Office Periods to allow the Effort Class, used when generating time entries, to be set.
- Updated: [Notes Export/Import](../../import/notes.html) Export of notes now also contain a column with the attachments of the notes.

## June 15, 2024

- Updated: [Mail API](../../requests/mail.html#parameters) added `#end` email parameter.
- Updated: [App Offering Mutations](https://developer.xurrent.com/graphql/mutation/appofferingcreate/#carddescription) added `cardDescription` field.
- Added: [appOfferingAutomationRuleDelete Mutation](https://developer.xurrent.com/graphql/mutation/appofferingautomationruledelete/) allowing deletion of automation rules defined on App Offerings.
- Updated: [App Offering](https://developer.xurrent.com/graphql/object/appoffering/) added support to configure an OAuth Authorization Grant Code token via `oauthAuthorizationEndpoints` and `grantType` on their scopes.

## June 8, 2024

- Updated: [Icons](../icons/index.html) added many new SVG icons to “Individual Icons”.
- Updated: [UI Extension Javascript API](../../ui_extensions/js_api.html) documented all properties of the ITRP object.

## May 18, 2024

- Updated: [Mail API](../../requests/mail.html) updated the Mail API rules with the new “Match on ID when found in the email subject” Email Policy options.

## May 3, 2024

- Deprecated: [UI Extension](https://developer.xurrent.com/graphql/object/uiextension/): [uiExtensionUpdate](https://developer.xurrent.com/graphql/mutation/uiextensionupdate/) deprecated `category` as input argument.

## April 27, 2024

- New: [UI Extension Javascript API](../../ui_extensions/js_api.html): added `service_instance` to the list of request fields that can be interacted with.
- Updated: [Export](../../export.html): Added additional clarification about architecting integrations based on export files.

## April 6, 2024

- Updated: [Tag](https://developer.xurrent.com/graphql/object/tag/): added `requestCount`.

## March 30, 2024

- Updated: [DiscoveredConfigurationItems Mutation](https://developer.xurrent.com/graphql/input_object/discoveredciinput/): added `service` argument to both [DiscoveredProductInput](https://developer.xurrent.com/graphql/input_object/discoveredproductinput/#service) and [DiscoveredCiInput](https://developer.xurrent.com/graphql/input_object/discoveredciinput/#service) allowing a service to be linked to discovered assets.

## March 23, 2024

- Updated: [Configuration Items](../../configuration_items/index.html),: added `archive`, `trash` and `restore` options.

## March 16, 2024

- Updated: [Request](https://developer.xurrent.com/graphql/object/request/): added `tags`
- Updated: [RequestCreate Mutation](https://developer.xurrent.com/graphql/mutation/requestcreate/): added `newTags`
- Updated: [RequestUpdate Mutation](https://developer.xurrent.com/graphql/mutation/requestupdate/): added `newTags` and `tagsToDelete`
- New: [Tags](../../requests/tags/index.html): Added tags to the REST API
- Updated: [Note](https://developer.xurrent.com/graphql/object/note/): added `inboundEmail`
- New: [Requests - Note attachments REST API](../../requests/note_attachments.html)
- New: [Requests - Inbound emails REST API](../../requests/inbound_emails.html)

## March 2, 2024

- Updated: [Broadcast](https://developer.xurrent.com/graphql/object/broadcast/): added the `organizations`, `skillPools` and `sites` connection
- Updated: [broadcastCreate Mutation](https://developer.xurrent.com/graphql/mutation/broadcastcreate/): added `organizationIds`, `skillPoolIds` and `siteIds`
- Updated: [broadcastUpdate Mutation](https://developer.xurrent.com/graphql/mutation/broadcastupdate/): added `organizationIds`, `skillPoolIds` and `siteIds`

## February 24, 2024

- Updated: [broadcastCreate Mutation](https://developer.xurrent.com/graphql/mutation/broadcastcreate/): added `requestId`
- Updated: [broadcastUpdate Mutation](https://developer.xurrent.com/graphql/mutation/broadcastupdate/): added `requestId`

## February 17, 2024

- Updated: [OAuth access token request](../../oauth/authorization_code_grant.html#access-token-request) and [OAuth refresh token request](../../oauth/authorization_code_grant.html#refresh-token-request) require their parameters to be passed via the **body**. If these parameters are passed via the query string it will result in an “Bad Request” response.

## February 10, 2024

- Updated: [projectTaskUpdate Mutation](https://developer.xurrent.com/graphql/mutation/projecttaskupdate/): added `phaseId`
- Updated: [taskCreate Mutation](https://developer.xurrent.com/graphql/mutation/taskcreate/): added `phaseId`
- Updated: [taskUpdate Mutation](https://developer.xurrent.com/graphql/mutation/taskupdate/): added `phaseId`

## February 3, 2024

- Updated: [RequestFilter](https://developer.xurrent.com/graphql/input_object/requestfilter/): deprecated `supplierRequestid`, please use `supplierRequestID` instead

## January 27, 2024

- Updated: [ServiceInstances](https://developer.xurrent.com/graphql/object/serviceinstance): added the `maintenanceWindow` and `timeZone` fields.
- Updated: [TaskFilter](https://developer.xurrent.com/graphql/input_object/taskfilter/#supplierrequestid). Tasks can be filtered on their `supplierRequestID`.

## January 13, 2024

- New: [ShopArticleCategories](https://developer.xurrent.com/graphql/object/shoparticlecategory). These new objects are also available for export/import.
- Updated: [ShopArticles](https://developer.xurrent.com/graphql/object/shoparticle): added the `category` field.

## December 16, 2023

- Removed: Backwards compatibility support using ‘change’ instead of ‘workflow’ has been completely removed.

## December 9, 2023

- Updated: [AgileBoardColumn](https://developer.xurrent.com/graphql/object/agileboardcolumn): added the `clearMember` field.
- Updated: [DiscoveredConfigurationItems Mutation](https://developer.xurrent.com/graphql/input_object/discoveredciinput/): It is no longer required to specify the `status` field of the Configuration Items to be uploaded.

## December 2, 2023

- Updated: [Change to Workflow](../change_to_workflow.html): The account settings that control whether the ‘change to workflow’ deprecations
 can be used in API integrations have now been disabled and removed from all environments.

## November 18, 2023

- New: [SlaCoverageGroup](https://developer.xurrent.com/graphql/object/slacoveragegroup/), [SlaCoverageGroupCreate](https://developer.xurrent.com/graphql/mutation/slacoveragegroupcreate/), [SlaCoverageGroupUpdate](https://developer.xurrent.com/graphql/mutation/slacoveragegroupupdate/).
- Updated: [ServiceLevelAgreement](https://developer.xurrent.com/graphql/object/servicelevelagreement/#coveragegroups): added the `coverageGroups` connection, added the `coverage_groups` value to [SlaCoverage](https://developer.xurrent.com/graphql/scalar/slacoverage/).
- Updated: [AgileBoard](https://developer.xurrent.com/graphql/object/agileboard/#customerrepresentativeslas): added the `customerRepresentativeSlas` connection.

## October 28, 2023

- Updated: [Survey](https://developer.xurrent.com/graphql/object/survey/) and [SurveyQuestion](https://developer.xurrent.com/graphql/object/surveyquestion/): added the `translations` connections.
- Updated: [Broadcast](https://developer.xurrent.com/graphql/object/broadcast/): added the `remarks`, `remarksAttachments` and `translations` fields.
- Updated: [PdfDesign](https://developer.xurrent.com/graphql/object/pdfdesign/): added the `description` and `descriptionAttachments` fields.
- Updated: [Service Offerings](../../service_offerings/index.html): added the `charge_type_case`, `rate_case`, `rate_case_currency`, `resolution_target_case`, `resolution_target_case_in_days`, `response_target_case`, `response_target_case_in_days` and `support_hours_case` fields.
- Updated: [Service Level Agreement](../../service_level_agreements.html): added the `activityID_case` field.

## October 23, 2023

- Updated: [Events API](../../requests/events.html): Added ability to set requested\_by value.

## October 14, 2023

- New: [NoteReaction](https://developer.xurrent.com/graphql/object/notereaction/), [noteReactionCreate](https://developer.xurrent.com/graphql/mutation/notereactioncreate/) and [noteReactionDelete](https://developer.xurrent.com/graphql/mutation/notereactiondelete/).
- Updated: [GraphQL documentation](https://developer.xurrent.com/graphql#rate-limits): Added the X-CostLimit headers.

## October 7, 2023

- Updated: [ConfigurationItem](https://developer.xurrent.com/graphql/object/configurationitem/): added the fields `lastSeenAt`, `endOfSupportDate`, `operatingSystem` and `ramAmount`. These fields can also be changed via mutations and used to filter configuration items.
- Updated: [DiscoveredConfigurationItems Mutation](https://developer.xurrent.com/graphql/mutation/discoveredconfigurationitems/): added the fields `lastSeenAt`, `endOfSupportDate`, `operatingSystemId`, `ramAmount`, `nrOfProcessors` and `nrOfCores`.
- Updated: [RequestFilter](https://developer.xurrent.com/graphql/input_object/requestfilter/): added [`operatingSystem`](https://developer.xurrent.com/graphql/input_object/requestfilter/#operatingsystem) to allow filtering requests based on the operating system of the linked configuration items.
- Updated: [Request](https://developer.xurrent.com/graphql/object/request/), [Task](https://developer.xurrent.com/graphql/object/task/) and [ProjectTask](https://developer.xurrent.com/graphql/object/projecttask/): added the `checkedItems` field.
- Updated: [AppOffering](https://developer.xurrent.com/graphql/object/appoffering/): added the `cardDescription` field.

## September 30, 2023

- Updated: [SyncSet](https://developer.xurrent.com/graphql/object/syncset/): added the [field `resolvedTypes`](https://developer.xurrent.com/graphql/object/syncset/#resolvedtypes) and the [`selectedRecords` connection](https://developer.xurrent.com/graphql/object/syncset/#selectedrecords).
- Updated: [ShortUrlDataType](https://developer.xurrent.com/graphql/scalar/shorturldatatype/): added the value `change_calendar_personal_view`.

## September 23, 2023

- New: [Waiting for Customer Follow-Ups](https://developer.xurrent.com/graphql/object/waitingforcustomerfollowup/) and [Waiting for Customer Rules](https://developer.xurrent.com/graphql/object/waitingforcustomerrule/).
- New: [Waiting for Customer Follow-Ups Import](../../import/waiting_for_customer_follow_ups/index.html).
- Updated: [Service Offerings](https://developer.xurrent.com/graphql/object/service_offering) added the fields `slaWaitingForCustomerFollowUp`.
- Updated: [Broadcasts](https://developer.xurrent.com/graphql/object/broadcast) added the `slas` field.

## September 9, 2023

- Updated: [PdfDesign](https://developer.xurrent.com/graphql/object/pdfdesign/): added the `source` and `sourceID` fields.
- Added: [Export](../../export.html) and [Import of PDF Designs](../../import/pdf_designs/index.html), by using type value `pdf_designs`.
- Deprecated:
 - [Service Level Agreement](https://developer.xurrent.com/graphql/object/servicelevelagreement) deprecated the `billingID` field in favor of the `agreementID` field.
 - [Time Entry](https://developer.xurrent.com/graphql/object/timeentry) deprecated the `billingID` and `chargeID` fields in favor of the `agreementID` and `rateID` fields.
 - Replaced [Effort Class Charge IDs](https://developer.xurrent.com/graphql/object/effortclasschargeid/) by [Effort Class Rate IDs](https://developer.xurrent.com/graphql/object/effortclassrateid/).

## September 2, 2023

- Updated: [Project](https://developer.xurrent.com/graphql/input_object/projectfilter): added the `phase` filter.
- Updated: [Standard Service Request](https://developer.xurrent.com/graphql/object/standardservicerequest): added the `resolutionTargetBestEffort` and `responseTargetBestEffort` fields.

## August 5, 2023

- Updated: [AppOffering](https://developer.xurrent.com/graphql/object/appoffering/): added the `requiresEnabledOauthPerson` field.
- Updated: [Person](https://developer.xurrent.com/graphql/object/person/): added the `oauthPersonEnablement` field.

## July 29, 2023

- Updated: [ReservationOffering](https://developer.xurrent.com/graphql/object/reservationoffering/): added the `private_reservations` field.
- Updated: [Site](../../sites.html): the fields `address`, `city`, `state`, `zip`, `country` and `integration` can now be updated via the REST API.

## July 22, 2023

- Updated: [UI Extension](https://developer.xurrent.com/graphql/object/uiextension/): [uiExtensionCreate](https://developer.xurrent.com/graphql/mutation/uiextensioncreate/) and [uiExtensionUpdate](https://developer.xurrent.com/graphql/mutation/uiextensionupdate/) allow `description` as input arguments.
- Updated: All GraphQL object types with a `description` field allow `descriptionAttachments` as input arguments.
- Updated: All GraphQL object types with a `remarks` field allow `remarksAttachments` as input arguments.

## July 8, 2023

- Updated: [Change to Workflow](../change_to_workflow.html): Added account settings to control whether the ‘change to workflow’ **deprecations** can be used in API integrations with the account:
 - Allow deprecated use of change in REST API
 - Allow deprecated use of change in GraphQL API
 - Allow deprecated use of change in Bulk API
 - Allow deprecated use of change in Mail API
 - Allow deprecated use of change in Webhooks API
- Updated: [Calendar](https://developer.xurrent.com/graphql/input_object/calendarfilter/): added the `name` filter.

## July 1, 2023

- Updated: [Currency](https://developer.xurrent.com/graphql/scalar/currency/) Added the `ghs` (Ghanaian Cedi) currency.

## June 3, 2023

- New: [UI Extensions Javascript API](../../ui_extensions/js_api.html): added `impact` to the list of form fields that can be interacted with.
- Updated: [UI Extension](https://developer.xurrent.com/graphql/object/uiextension/): added the `createdBy` and `updatedBy` fields.
- Updated: [UI Extension](https://developer.xurrent.com/graphql/input_object/uiextensionfilter/): added the `createdBy` and `updatedBy` filters.

## May 20, 2023

- Updated: [PermissionRole](https://developer.xurrent.com/graphql/scalar/permissionrole/) added the
 `worflow_automator_auditor` and `workflow_automator_specialist` roles.
- New: [SyncSet](https://developer.xurrent.com/graphql/object/syncset/)

## May 13, 2023

- Updated: [TaskApproval](https://developer.xurrent.com/graphql/object/taskapproval/): added the `attachment` field.

## May 6, 2023

- Updated: [Project](https://developer.xurrent.com/graphql/object/project/): added the `portfolio_insight` view.

## April 22, 2023

- Updated: [Request](https://developer.xurrent.com/graphql/object/request/): [requestCreate](https://developer.xurrent.com/graphql/mutation/requestcreate/) and [requestUpdate](https://developer.xurrent.com/graphql/mutation/requestupdate/) allow `knowledgeArticleIds` as input arguments.
- Deprecated:
 - [Request](https://developer.xurrent.com/graphql/object/request) deprecated the `knowledgeArticle` field in favor of the `knowledgeArticles` field.

## April 15, 2023

- Added: [Export](../../export.html) and [Import](../../import.html) of [Custom Views](../../import/custom_views.html).
- Removed: [Requests](../../requests.html#list-requests-relevant-for-api-user) removed the unused retrieval option `requests_of_my_organization`.

## April 8, 2023

- New: [KnowledgeArticleTemplate](https://developer.xurrent.com/graphql/object/knowledgearticletemplate/)
- Updated: [KnowledgeArticle](https://developer.xurrent.com/graphql/object/knowledgearticle/): added the `customFields` and `template` fields.
- Updated: [Knowledge Article](https://developer.xurrent.com/graphql/input_object/knowledgearticlefilter/): added the `template` and `customFilters` filters.
- New: [Access attributes of selected items via metadata fields of custom views](../../ui_extensions/js_api.html#access-attributes-of-selected-items-via-metadata-fields-of-custom-views).

## April 1, 2023

- Updated: [Invoice](https://developer.xurrent.com/graphql/object/invoice/): added the `financialID` field.
- Updated: [Invoice](https://developer.xurrent.com/graphql/input_object/invoicefilter/): added the `financialID` filter.

## March 25, 2023

- Updated: [Effort Class](https://developer.xurrent.com/graphql/object/effortclass/): added the `skillPools` connection.
- Updated: [Skill Pool](https://developer.xurrent.com/graphql/object/skillpool/): added the `effortClasses` connection.
- Updated: [Workflow](https://developer.xurrent.com/graphql/input_object/workflowfilter/): added the `phase` filter.

## March 18, 2023

- New: Added fields related to charges.
 - Added charge related fields to [Service Offering](https://developer.xurrent.com/graphql/object/serviceoffering/)
 - Added charge related fields to [Standard Service Request](https://developer.xurrent.com/graphql/object/standardservicerequest/)
 - Added charges to [Time Entry](https://developer.xurrent.com/graphql/object/timeentry/)
 - [Effort Class Rates](https://developer.xurrent.com/graphql/object/effortclassrate/)
- Updated: [DiscoveredConfigurationItems Mutation](https://developer.xurrent.com/graphql/mutation/discoveredconfigurationitems/): added the `DEFAULT` [strategy](https://developer.xurrent.com/graphql/enum/discovereditemstrategy/).

## March 11, 2023

- Updated: [Standard Service Request](https://developer.xurrent.com/graphql/object/standardservicerequest/): added the `slaNotificationScheme` field.
- Updated: [Configuration Item](https://developer.xurrent.com/graphql/object/configurationitem/): added the `workflowTemplate`, `recurrence` and `workflowManager` fields.
- Updated: [Product](https://developer.xurrent.com/graphql/object/product/): added the `workflowTemplate`, `recurrence` and `workflowManager` fields.
- Updated: [Recurrence](https://developer.xurrent.com/graphql/object/recurrence/): added the `calendar` field.

## March 4, 2023

- Updated: [Request](https://developer.xurrent.com/graphql/input_object/requestfilter) added the `workflowCategory`, `workflowTemplate` and `workflowType` filters.

## February 25, 2023

- The meaning of the [`all` KnowledgeArticleView value](https://developer.xurrent.com/graphql/enum/knowledgearticleview/#all) was updated. This view now also includes all knowledge articles provided by other accounts to the current user. This matches the old `provided_to_me` view, which is now deprecated. The new [`managed_in_this_account` view](https://developer.xurrent.com/graphql/enum/knowledgearticleview/#managed_in_this_account) matches the old `all` view (which is identical to the default `current_account`).

## February 18, 2023

- Added `in_progress` as new value in [WorkflowStatus](https://developer.xurrent.com/graphql/scalar/workflowstatus/), also applicable for the status field for [Worfklows](../../workflows.html#fields) and [Releases](../../releases.html#fields).
- Added: The field `requested_by` to the [ShopOrderLine](../../shop_order_lines/index.html#fields) REST API and the [ShopOrderLine](https://developer.xurrent.com/graphql/object/shoporderline) GraphQL API.

## February 11, 2023

- Updated: [Request](https://developer.xurrent.com/graphql/object/request/): added the `knowledgeArticles` connection.

## February 4, 2023

- New: Ability to view, create and delete [Request Watches](../../requests/watches.html)
- Updated: [EffortClass](https://developer.xurrent.com/graphql/object/effortclass/): added the `serviceOfferings` connection. [effortClassCreate](https://developer.xurrent.com/graphql/mutation/effortclasscreate/) and [effortClassUpdate](https://developer.xurrent.com/graphql/mutation/effortclassupdate/) allow `serviceOfferingIds` as input arguments.

## January 28, 2023

- Updated: [TaskFilter](https://developer.xurrent.com/graphql/input_object/taskfilter) added the `skillPool` filter.
- New: Ability to [create notes](https://developer.xurrent.com/graphql/mutation/notecreate/) via the GraphQL API.
- New: Added fields related to billing identifiers to the GraphQL API
 - Added billing ID, charge ID and activity ID to [Service Level Agreement](https://developer.xurrent.com/graphql/object/servicelevelagreement/)
 - Added billing ID, charge ID and activity ID to [Time Entry](https://developer.xurrent.com/graphql/object/timeentry/)
 - [Effort Class Charge IDs](https://developer.xurrent.com/graphql/object/effortclasschargeid/)
 - [Standard Service Request Activity IDs](https://developer.xurrent.com/graphql/object/standardservicerequestactivityid/)
- New: Added fields related to billing identifiers to the REST API
 - Added billing ID, charge ID and activity ID to [Service Level Agreement](../../service_level_agreements.html)
 - Added billing ID, charge ID and activity ID to [Time Entry](../../time_entries.html)
 - [Effort Class Charge IDs](https://developer.xurrent.com/v1/service_level_agreements/effort_class_chargeIDs/)
 - [Standard Service Request Activity IDs](../../service_level_agreements/standard_service_request_activityIDs/index.html)
- New: [SLA Financial Details import](../../import/slas_financial_details/index.html), [SLA Charges import](../../import/slas_charges/index.html) and [SLA Activities import](../../import/slas_activities/index.html).
- Updated: Added `suppress_note_added_notifications` to the `notes` endpoints of all record types that support notes, for example [Request - Notes](../../requests/notes/index.html).
- Updated: [Request - Notes](../../requests/notes/index.html): added the `internal` field.
- Updated: [DiscoveredConfigurationItems Mutation](https://developer.xurrent.com/graphql/mutation/discoveredconfigurationitems/): added the `remarks` input argument.

## January 21, 2023

- Updated: [TaskTemplate](https://developer.xurrent.com/graphql/object/tasktemplate/): added category `automation`.
- Updated: [Task](https://developer.xurrent.com/graphql/object/task/): added category `automation`.
- Updated: [Service Level Agreement](https://developer.xurrent.com/graphql/object/servicelevelagreement/): added the `customerAccount` field.
- Updated: [FirstLineSupportAgreement](https://developer.xurrent.com/graphql/object/firstlinesupportagreement): documented the `pickupTarget`,
 `pickupsWithinTarget`, `rejectedSolutions`, `serviceDeskOnlyResolutions`, `serviceDeskResolutions` fields.
- Updated: [Webhook](https://developer.xurrent.com/graphql/object/webhook/) GraphQL API: added the `source` and `sourceID` fields.
- Updated: [Webhooks](../../webhooks/events.html) REST API: added the `source`, `sourceID` and `webhook_policy` fields.
- Added: Ability to [delete webhooks](https://developer.xurrent.com/graphql/mutation/webhookdelete/) and [webhook policies](https://developer.xurrent.com/graphql/mutation/webhookpolicydelete/) to the GraphQL API.
- Updated: [UiExtension](https://developer.xurrent.com/graphql/object/uiextension/) added the `description` field.
- Updated: [OrganizationFilter](https://developer.xurrent.com/graphql/input_object/organizationfilter/) added the `businessUnitOrganization` filter.

## January 14, 2023

- Updated: [FirstLineSupportAgreement](https://developer.xurrent.com/graphql/object/firstlinesupportagreement) added the `supportChatPickupTarget` field.
- Updated: [Mail API](../../requests/mail.html) The number of days that a received email may be added as a note to an existing
 completed record is no longer fixed to 28 days, but can now be configured by account administrators on the Self Service Settings form.

## January 7, 2023

- Updated: [Export API](../../export.html): add `line_separator` parameter.

## December 31, 2022

- New: As an account administrator or account designer you can now copy the NodeID from the actions menu of a record in Xurrent.
- Updated: [ServiceOffering](https://developer.xurrent.com/graphql/object/serviceoffering/): added the `defaultEffortClass` field and the `effortClasses` connection.
- Updated: [Service Level Agreements](../../service_level_agreements.html) added the `service_instances` relation.

## December 17, 2022

- Updated: [TaskFilter](https://developer.xurrent.com/graphql/input_object/taskfilter) added the `taskTemplate` filter.
- Updated: [Person](https://developer.xurrent.com/graphql/object/person) added the `guest` field.
- Updated: [Events API](../../requests/events.html) documented which parameters can be used to update an existing request.

## December 10, 2022

- New: [ShopArticles](https://developer.xurrent.com/graphql/object/shoparticle). These new objects are also available for export/import.
- New: [ShopOrderLines](https://developer.xurrent.com/graphql/object/shoporderline). These new objects are also available for export/import.
- Updated: [Organization](https://developer.xurrent.com/graphql/object/organization/): added the `orderTemplate` field.
- Updated: [Request](https://developer.xurrent.com/graphql/object/request/): added categories `order` and `fulfillment`.
- Updated: [TaskTemplate](https://developer.xurrent.com/graphql/object/tasktemplate/): added category `fulfillment_placeholder`.
- Updated: [Workflow](https://developer.xurrent.com/graphql/object/workflow/): added category `order` and justification `purchase`.
- Updated: [WorkflowTemplate](https://developer.xurrent.com/graphql/object/workflowtemplate/): added category `order` and justification `purchase`.

## December 3, 2022

- New: GraphQL support for uploading attachments. [`attachmentStorage`](https://developer.xurrent.com/graphql/object/attachmentstorage/) allows retrieval of parameters for uploading. Once uploaded the attachments can be used for: [custom fields](https://developer.xurrent.com/graphql/mutation/requestcreate/#customfieldsattachments), [request notes](https://developer.xurrent.com/graphql/mutation/requestcreate/#noteattachments) and [task instructions](https://developer.xurrent.com/graphql/mutation/taskcreate/#instructionsattachments) and [notes](https://developer.xurrent.com/graphql/mutation/taskcreate/#noteattachments).
- New: People can now also be filtered on [`jobTitle`](https://developer.xurrent.com/graphql/input_object/personfilter/#jobtitle).

## November 26, 2022

- New: [SLA Notification Schemes](https://developer.xurrent.com/graphql/object/slanotificationscheme/) and [SLA Notification Rules](https://developer.xurrent.com/graphql/object/slanotificationrule/).
- New: [SLA Notification Schemes Import](../../import/sla_notification_schemes/index.html).
- Updated: [Service Offerings](https://developer.xurrent.com/graphql/object/service_offering) added the fields `slaNotificationSchemeLow`, `slaNotificationSchemeMedium`, `slaNotificationSchemeHigh` and `slaNotificationSchemeTop`.
- Documented `..._nodeID` fields in [Webhooks](../../webhooks.html).

## November 12, 2022

- Updated: [Organization](https://developer.xurrent.com/graphql/object/organization) added the `contracts` connection.
- Deprecated:
 - [Product](https://developer.xurrent.com/graphql/object/product) deprecated the `category` field in favor of the `productCategory` field.

## November 5, 2022

- Updated [Enumerations](../enumerations/index.html) The word `violate` has been renamed to `breach` in several keys of the `report.standard` enumeration.
- Updated: [PersonFilter](https://developer.xurrent.com/graphql/input_object/personfilter) added the `guest` filter
- Deprecated:
 - Querying [Workflow Object](https://developer.xurrent.com/graphql/object/workflow) records using the `changes` connection has been deprecated in favor of the `workflows` connection.
 - Querying [WorkflowType Object](https://developer.xurrent.com/graphql/object/workflowtype) records using the `changeTypes` connection has been deprecated in favor of the `workflowTypes` connection.
 - Querying [WorkflowTemplate Object](https://developer.xurrent.com/graphql/object/workflowtemplate) records using the `changeTemplates` connection has been deprecated in favor of the `workflowTemplates` connection.

## October 29, 2022

- Updated: [DiscoveredConfigurationItems Mutation](https://developer.xurrent.com/graphql/mutation/discoveredconfigurationitems/): added the `alternativeSources` input argument.

## October 8, 2022

- New: [ScrumWorkspaces](https://developer.xurrent.com/graphql/object/scrumworkspace), [Sprints](https://developer.xurrent.com/graphql/object/sprint) and [SprintBacklogItems](https://developer.xurrent.com/graphql/object/sprintbacklogitem). These new objects are also available for export/import.
- Updated: [Team](https://developer.xurrent.com/graphql/object/team/): added the `scrumWorkspace` field.
- Updated: [Agile Board](https://developer.xurrent.com/graphql/object/agileboard/): added the `currentSprint` field.
- Updated: [Request](https://developer.xurrent.com/graphql/object/request/), [Problem](https://developer.xurrent.com/graphql/object/problem/), [Task](https://developer.xurrent.com/graphql/object/task/) and [Project Task](https://developer.xurrent.com/graphql/object/projecttask/): added the `sprintBacklogItems` connection.

## October 1, 2022

- Updated [TimeEntry](https://developer.xurrent.com/graphql/object/timeentry/): added the `started_at` field.

## September 24, 2022

- Updated [Task Template](https://developer.xurrent.com/graphql/object/tasktemplate/) & [Task](https://developer.xurrent.com/graphql/object/task/): added the `noteBehavior` field.
- Updated [Project Task Template](https://developer.xurrent.com/graphql/object/projecttasktemplate/) & [Project Task](https://developer.xurrent.com/graphql/object/projecttask/): added the `noteBehavior` field.
- Updated [ServiceInstance](https://developer.xurrent.com/graphql/object/serviceinstance/): added the `pictureUri` field.

## September 8, 2022

- Updated: [RequestFilter](https://developer.xurrent.com/graphql/input_object/requestfilter) added the `lastNoteByRequester` filter

## July 23, 2022

- Updated: [Currency](https://developer.xurrent.com/graphql/scalar/currency) added the Chilean Peso (`clp`) currency.

## July 16, 2022

- Updated: [OAuth - Client Credentials Grant](../../oauth/client_credentials_grant.html) Xurrent’ss response will have a HTTP status code 400 in case an invalid token request is made.

## July 2, 2022

- Updated: [Adding a note to an existing record](../../requests/mail.html#adding-a-note-to-an-existing-record) using the Mail API

## June 22, 2022

- Updated: [RequestTemplateFilter](https://developer.xurrent.com/graphql/input_object/requesttemplatefilter) added the `uiExtension` filter

## June 15, 2022

- Added: [Rate limit documentation](../../export.html#rate-limit) for the [Export API](../../export.html).

## June 10, 2022

- Added: `Internal Notes` column to [Requests Import](../../import/requests.html)

## May 14, 2022

- Added: [ProductBacklogItem](https://developer.xurrent.com/graphql/interface/productbacklogitem/) added the `productBacklogEstimate` field.
- Updated: [ProductBacklog](https://developer.xurrent.com/graphql/object/productbacklog/) renamed `productGoal` and `productGoalAttachments` into `description` and `descriptionAttachments`.

## May 7, 2022

- [Pagination](../pagination.html): Removed deprecation warning about manual pagination using the `page` parameter.

## April 30, 2022

- Updated [Mail API](../../requests/mail.html#custom-fields): Described usage of custom fields.

## April 23, 2022

- Removed: [ConfigurationItem](https://developer.xurrent.com/graphql/object/configurationitem) Removed the `startDate` field, which was deprecated October 16th 2021. The `inUseSince` field should be used instead. This also means the `start_date` field is also no longer available in the REST API, import/export, automation rules and the JavaScript API for UI extensions.

## April 16, 2022

- Updated [attachments documentation](../data_types.html#attachments): the [.Net SDK](https://github.com/code4me/4me-sdk-csharp) now also offers attachment support.
- Updated [Task Template](https://developer.xurrent.com/graphql/object/tasktemplate/) & [Task](https://developer.xurrent.com/graphql/object/task/): added the `providerNotAccountable` field and filter.

## April 9, 2022

- Updated [Request](https://developer.xurrent.com/graphql/object/request/) & [Affected Sla](https://developer.xurrent.com/graphql/object/affectedsla/): added the `providerNotAccountable` and `providerWasNotAccountable` fields and filters.
- Updated [Period](https://developer.xurrent.com/graphql/object/period/): added the `providerNotAccountable` field.
- Updated [App Offering](https://developer.xurrent.com/graphql/object/appoffering): added the `configurationUriTemplate` field.

## April 2, 2022

- Changed: Version 2.0.0 of the [C# SDK for Xurrent](../libraries.html) has been released, and is now also available as a [NuGet package](https://www.nuget.org/packages/Sdk4me/).
- Added: [Export](../../export.html) added `generic_project_task_automation_rules` to the list of available types.
- Added: [AutomationRules](https://developer.xurrent.com/graphql/object/automationrule/#fields) `project_task` to the possible values of the `generic` field.

## March 26, 2022

- Added: [Workflow](https://developer.xurrent.com/graphql/object/workflow/#connections-1) added the `automationRules` connection.
- Added: [WorkflowTemplates](https://developer.xurrent.com/graphql/object/workflowtemplate/#connections-1) added the `automationRules` connection.
- Changed: The [Workflow Templates - Automation Rules API](../../workflow_templates/automation_rules.html) no longer returns automation rules that are linked to task templates of the workflow template. Use the [Workflow Templates - Task Template Automation Rules API](../../workflow_templates/task_template_automation_rules.html) instead.
- Deprecated: [Tasks API](../../tasks.html) the undocumented `initial_note` attribute will be removed from the API on **April 23, 2022** in QA and **April 30, 2022** in Production.
 To retrieve the initial note of a task, use the [Tasks - Notes API](../../tasks/notes/index.html) instead.

## March 19, 2022

- Updated: [Languages](https://developer.xurrent.com/graphql/scalar/language) added the Lithuanian language.
- Documented `on_backlog` as possible status value for [Requests](../../requests.html) and [Problems](../../problems.html).
- Documented `..._attachments` field in various REST API endpoints.

## March 12, 2022

- New: [Product Backlogs](https://developer.xurrent.com/graphql/object/productbacklog/)
 - [Root connection](http://localhost:4000/graphql/object/productbacklog/#root-connection-1), [productBacklogCreate](https://developer.xurrent.com/graphql/mutation/productbacklogcreate/) and [productBacklogUpdate](https://developer.xurrent.com/graphql/mutation/productbacklogupdate/) mutations.
 - [Product Backlog Import](../../import/product_backlogs/index.html) and [Product Backlog Item Import](../../import/product_backlog_items/index.html)
 - [Requests](https://developer.xurrent.com/graphql/object/request/#productbacklog) and [Problems](https://developer.xurrent.com/graphql/object/problem/#productbacklog) added the `productBacklog` and `productBacklogPosition` fields.
- Updated: [Languages](https://developer.xurrent.com/graphql/scalar/language) added the Macedonian language.
- Documented `skill_pool` field for [Project Tasks](../../project_tasks.html) and [Project Task Templates](../../project_task_templates.html).
- Documented `information_attachments` field for [Project Categories](../../project_categories/index.html) and [Project Risk Levels](../../project_risk_levels/index.html).
- Updated description of how to add, update and delete [Project Phases](../../projects/phases.html) and [Project Template Phases](../../project_templates/phases/index.html).

## March 5, 2022

- Added: [Service Level Agreement](https://developer.xurrent.com/graphql/object/servicelevelagreement/#connections-1) added the `customerRepresentatives` connection.
- Deprecated:
 - The [Service Level Agreement GraphQL API](https://developer.xurrent.com/graphql/object/servicelevelagreement/#fields-1) has deprecated the `customerRepresentative` field in favor of the `customerRepresentatives` connection.
 - The `customer_rep` field of the [Service Level Agreements API](../../service_level_agreements.html) has been deprecated in favor of the [Service Level Agreements - Customer Representatives API](../../service_level_agreements/customer_representatives.html)
 - The “Customer Representative” column in [exports and imports of service level agreements](../../import/slas.html) has been deprecated in favor of the “Customer Representatives” column.
 - The deprecated fields will be removed from the APIs on **June 4, 2022**.

## February 26, 2022

- Added: [Workflow Templates - Task Template Relations API](../../workflow_templates/task_template_relations.html)
- Updated [Discovery Tools](../../import/discovery_tools/index.html) to mention that discovered Configuration Items can be linked to manually entered Products based on `productID` using the [discoveredConfigurationItems mutation](https://developer.xurrent.com/graphql/mutation/discoveredconfigurationitems/).
- Changed: As of February 19, REST API text and string filters are case sensitive, unless otherwise specified. Note: until now, the behavior of these filters was implicit and undocumented. When we recently discovered that these filters were in fact case insensitive, this was treated as a bug, which is why it was not previously announced. We apologize for any inconvenience this may have caused.
- Updated: [Currency](https://developer.xurrent.com/graphql/scalar/currency) added the Omani Rial (OMR) currency.

## February 12, 2022

- Updated the name of some GraphQL mutation arguments for arrays of identifiers to end on `...Ids` so they are inline with the generic naming convention:
 - Request mutations’ `configurationItems` to [configurationItemIds](https://developer.xurrent.com/graphql/mutation/requestcreate/#configurationitemids).
 - Calendar mutations’ `holidays` to [holidayIds](https://developer.xurrent.com/graphql/mutation/calendarcreate/#holidayids).
 - Workflow/Change mutations’ `requests` to [requestIds](https://developer.xurrent.com/graphql/mutation/workflowcreate/#requestids) and `problems` to [problemIds](https://developer.xurrent.com/graphql/mutation/workflowcreate/#problemids).
 - Task template mutations’ `serviceInstances` to [serviceInstanceIds](https://developer.xurrent.com/graphql/mutation/tasktemplatecreate/#serviceinstanceids).
- Removed: [Workflow](https://developer.xurrent.com/graphql/object/workflow) the fields `effortIndication` and `remainingEffort`, that were deprecated on October 2, 2021, have been removed.
- Updated: [Team](https://developer.xurrent.com/graphql/object/team) added the `autoAssign` field.
- Updated: [Person](https://developer.xurrent.com/graphql/object/person) added the `excludeTeamNotifications` field.

## February 5, 2022

- Updated: [Note](https://developer.xurrent.com/graphql/object/note/) added the option `outbound_email` to the `medium` field.

## January 29, 2022

- Updated: [RequestTemplate](https://developer.xurrent.com/graphql/object/requesttemplate) added the `assign_after_workflow_completion` field.
- Updated: [WorkflowTemplate](https://developer.xurrent.com/graphql/object/workflowtemplate) added the `assign_relations_to_workflow_manager` field.
- Updated: [DiscoveredProductInput](https://developer.xurrent.com/graphql/input_object/discoveredproductinput/) added the `productID` field.
- Updated: [Task](https://developer.xurrent.com/graphql/object/task) added the `failureTask` field.
- Updated: [WorkflowTaskTemplateRelation](https://developer.xurrent.com/graphql/object/workflowtasktemplaterelation) added the `failureTaskTemplate` field.

## January 15, 2022

**Important**: ‘Change’ has been renamed to ‘Workflow’ throughout all Xurrent APIs.

- ‘Change’ has been renamed to ‘Workflow’ throughout all Xurrent APIs.
- All API endpoints and usage of attributes which contain the word ‘change’ are now **deprecated**.
 Backward compatibility will be maintained **until February 4, 2023**.

 Read more about the details of this adjustment on the [Change to Workflow](../change_to_workflow.html) page.
- Note that there are a few (minor) breaking changes.
 Although we do not expect any customers to be affected by these breaking changes,
 please read through the corresponding section of the [Change to Workflow](../change_to_workflow.html#breaking-changes) page
 to ensure that you are not affected.
- Updated: [Currency](https://developer.xurrent.com/graphql/scalar/currency) added the Bosnia and Herzegovina Convertible Mark (BAM) currency.

## Jan 08, 2022

- Updated: [ConfigurationItemFilter](https://developer.xurrent.com/graphql/input_object/configurationitemfilter) added the `contract` filter
- Updated: [ServiceFilter](https://developer.xurrent.com/graphql/input_object/servicefilter) added the `account` filter
- Updated: [ServiceInstanceFilter](https://developer.xurrent.com/graphql/input_object/serviceinstancefilter) added the `account` filter

## December 25, 2021

- Removed: `asyncQueries` connection from the GraphQL API, and the associated filter and scope ‘async-query:Read’. These were accidentally added with the [discoveredConfigurationItems mutation](https://developer.xurrent.com/graphql/mutation/discoveredconfigurationitems/) on December 11th. The [asyncQuery field](https://developer.xurrent.com/graphql/mutation/discoveredconfigurationitems/#asyncquery) is the only supported way to access the asynchronous query execution.

## December 11, 2021

- New: [discoveredConfigurationItems mutation](https://developer.xurrent.com/graphql/mutation/discoveredconfigurationitems/). This mutation is especially designed to facilitate bulk upload of new and updated configuration item information. As such it is intended as an alternative to the use of the import API as described in [Discovery Tools](../../import/discovery_tools/index.html).
- Updated: [UI Extension Javascript API](../../ui_extensions/js_api.html) added the possibility to interact with the `asset` (Configuration items) field of problems and tasks.
- Added: The field `allow_repeat` to the [Reservation Offerings](../../reservation_offerings/index.html#fields) REST API and the [ReservationOffering](https://developer.xurrent.com/graphql/object/reservationoffering) GraphQL API.
- Added: The fields `recurrence` and `only_this_occurrence` to the [Reservations](../../reservations.html#fields) REST API and the [Reservation](https://developer.xurrent.com/graphql/object/reservation) GraphQL API.

## December 4, 2021

- Removed: the Xurrent REST API can no longer be accessed by providing an API token
 using Basic Authentication or query parameter.
- New: [Webhooks](../../webhooks/events.html) added the following events:
 - `request.agile-board-column-changed`
- Updated: [OrganizationFilter](https://developer.xurrent.com/graphql/input_object/organizationfilter) added the `parent` filter.
- Updated: [WorkflowFilter](https://developer.xurrent.com/graphql/input_object/workflowfilter) added the `project` filter.

## November 27, 2021

- Updated: [SCIM Provisioning](../../scim.html) Anyone with the account administrator role is now able configure SCIM.
 Previously, only the account *owner* was allowed to do this.
- Added a [section on variables](https://developer.xurrent.com/graphql/#variables-1) to the main GraphQL API page to highlight this feature of GraphQL
 and the security benefits it provides.

## November 13, 2021

- Updated: [ServiceFilter](https://developer.xurrent.com/graphql/input_object/servicefilter) added the
 `availabilityManager`, `capacityManager`, `workflowManager`,
 `continuityManager`, `knowledgeManager`, `problemManager` and `releaseManager`
 filters.
- Updated: added the `mentioningMe` filter to the following GraphQL input objects:
 - [WorkflowFilter](https://developer.xurrent.com/graphql/input_object/workflowfilter)
 - [ProblemFilter](https://developer.xurrent.com/graphql/input_object/problemfilter)
 - [ProjectFilter](https://developer.xurrent.com/graphql/input_object/projectfilter)
 - [ProjectTaskFilter](https://developer.xurrent.com/graphql/input_object/projecttaskfilter)
 - [ReleaseFilter](https://developer.xurrent.com/graphql/input_object/releasefilter)
 - [RequestFilter](https://developer.xurrent.com/graphql/input_object/requestfilter)
 - [RiskFilter](https://developer.xurrent.com/graphql/input_object/riskfilter)
 - [TaskFilter](https://developer.xurrent.com/graphql/input_object/taskfilter)
- Updated: [UI Extension Javascript API](../../ui_extensions/js_api.html) added the possibility to interact with the `status` field
 of requests, problems, tasks and project tasks.

## November 6, 2021

- Updated: The phrase ‘Most available fields for each model can be used in filters’ has been removed from the [Filtering](../filtering.html) page.
 Instead, a new section “Filtering” has been added to the documentation page of each of the record types that are
 available via the REST API, which explicitly lists the fields that can be used in filters.
 If you need more extensive filtering capabilities, you are encouraged to use the [Xurrent GraphQL API](https://developer.xurrent.com/graphql).
- Updated: [GraphQL API](https://developer.xurrent.com/graphql/) Added filters to several record types, so that the GraphQL API now supports
 all of the REST API filters (and many more).
- Deprecated: [Pagination](../pagination.html) by manually incrementing the `page` parameter is now deprecated.
 Most REST API endpoints will migrate to cursor based pagination, and to make sure that you are prepared, you should
 start using the URLs of the Link Header as soon as possible.
 **Support for manually incrementing the `page` parameter will be removed from the APIs on May 7, 2022.**
 You can continue to use the `page` parameter, but you **must** go through the pages in order.
 See [Pagination](../pagination.html) for more details.
- Removed: [Pagination](../pagination.html) The Link Header no longer contains a link to the last page of results.
 The preferred way to access the last page of results is to reverse the [sort order](../ordering.html),
 by flipping the minus signs.
 For example, the sort order `-status,-impact,created_at,id` can be reversed to `status,impact,-created_at,-id`.
- Added: The field `resolution_duration` to the following REST APIs:
 - [Requests](../../requests.html#fields)
 - [Problems](../../problems.html#fields)
 - [Workflows](../../workflows.html#fields)
 - [Tasks](../../tasks.html#fields)
 - [Projects](../../projects/index.html#fields)
 - [Project Tasks](../../project_tasks.html#fields)
 - [Risks](../../risks.html#fields)

## October 23, 2021

- Updated: [PersonFilter](https://developer.xurrent.com/graphql/input_object/personfilter) added the `billable` filter.
- Updated: [ShortUrl](https://developer.xurrent.com/graphql/object/shorturl) added `service_survey` as value for the `dataType` of a short url.

## October 16, 2021

- Updated: [ConfigurationItem](https://developer.xurrent.com/graphql/object/configurationitem) Introduced the `inUseSince` field, this will replace the (now deprecated) `startDate` field.
- Updated: [invoiceCreate Mutation](https://developer.xurrent.com/graphql/mutation/invoicecreate) and [invoiceUpdate Mutation](https://developer.xurrent.com/graphql/mutation/invoiceupdate) added the `serviceId` field.

## October 9, 2021

- Updated: [ConfigurationItem](https://developer.xurrent.com/graphql/object/configurationitem) added the `alternateNames` field.
- Updated: [ConfigurationItemFilter](https://developer.xurrent.com/graphql/input_object/configurationitemfilter) added the `alternateNames` and `productModel` filters.
- Updated: [ProductFilter](https://developer.xurrent.com/graphql/input_object/productfilter) added the `model` filter.
- Updated: [InvoiceFilter](https://developer.xurrent.com/graphql/input_object/invoicefilter) added the `invoiceNr`, `poNr` and `usefulLife` filters.
- Updated: [KnowledgeArticle](https://developer.xurrent.com/graphql/object/knowledgearticle) added the `updatedBy` field.
- Updated: [KnowledgeArticleFilter](https://developer.xurrent.com/graphql/input_object/knowledgearticlefilter) added the `updatedBy` filter.
- Updated: [ConfigurationItemRelation](https://developer.xurrent.com/graphql/object/configurationitemrelation) added the `source` field.
- Updated: [Invoice](../../invoices.html) added the `invoice_type` field.

## October 2, 2021

- Updated: [Invoice](https://developer.xurrent.com/graphql/object/invoice) added the field `depreciationStart`.
- Updated: [ProductCategoryFilter](https://developer.xurrent.com/graphql/input_object/productcategoryfilter/) added the `ruleSet` filter.
- Updated: [Workflow](https://developer.xurrent.com/graphql/object/workflow) added the field `actualVsPlannedEffortPercentage`.
- Deprecated: [Workflow](https://developer.xurrent.com/graphql/object/workflow) deprecated the `effortIndication` and `remainingEffort` fields in favor of `actualVsPlannedEffortPercentage`. The deprecated fields are still present in the APIs but always contain the value `0`.
 **The deprecated fields will be removed from the APIs on February 5, 2022.**
- Updated: [WorkflowOrderField](https://developer.xurrent.com/graphql/enum/workfloworderfield) added the `actualVsPlannedEffortPercentage` sort order, removed the `effortIndication` and `remainingEffort` sort orders.
- Updated: Added the `plannedEffort` field to [Problem](https://developer.xurrent.com/graphql/object/problem), [Request](https://developer.xurrent.com/graphql/object/request) and [RequestTemplate](https://developer.xurrent.com/graphql/object/requesttemplate).

## September 25, 2021

- Updated: [Invoice](https://developer.xurrent.com/graphql/object/invoice) added the fields `amortize`, `amortizationStart`, `amortizationEnd`, `configurationItems`, `depreciationMethod`, `poNr`, `rate`, `usefulLife`, and `salvageValue`.
- Updated: [Product](https://developer.xurrent.com/graphql/object/product) added the field `salvageValue`.
- Updated: [Workflow](https://developer.xurrent.com/graphql/object/workflow) added the `invoices` association.
- Updated: [Project](https://developer.xurrent.com/graphql/object/project) added the `invoices` association.
- Updated: [ServiceLevelAgreement](https://developer.xurrent.com/graphql/object/servicelevelagreement) added the `invoices` association.
- Updated: [FirstLineSupportAgreement](https://developer.xurrent.com/graphql/object/firstlinesupportagreement) added the `invoices` association.
- Updated: [ConfigurationItem](https://developer.xurrent.com/graphql/object/configurationitem) added the `invoices` association, and removed fields `poNr`, `purchaseValue`, `rate`, `salvageValue`, `usefulLife`, and `depreciationMethod`.
- Updated: [Contract](https://developer.xurrent.com/graphql/object/contract) added the `invoices` association.

## September 11, 2021

- Updated: [AffectedSlaFilter](https://developer.xurrent.com/graphql/input_object/affectedslafilter/) added the `requestedFor` filter.
- Updated: [Mail API](../../requests/mail.html#adding-a-note-to-an-existing-record-based-on-id-in-subject) updated rules for matching numbers in the subjects to existing records.

## August 28, 2021

- Updated: [AffectedSlaFilter](https://developer.xurrent.com/graphql/input_object/affectedslafilter/) added the `slaCustomerRegion` filter.
- Updated: [RequestFilter](https://developer.xurrent.com/graphql/input_object/affectedslafilter/) added the `slaCustomerRegion` filter.
- Removed: [InvoiceOrderField](https://developer.xurrent.com/graphql/enum/invoiceorderfield) removed ability to sort on the `invoiceableSubject` field.
- Updated: [Holidays Import](../../import/holidays.html) renamed the `From` / `Until` columns to `Start At` / `End At`
 for consistency with the [REST API](../../holidays.html) and [GraphQL API](https://developer.xurrent.com/graphql/object/holiday).
- New: [Survey](https://developer.xurrent.com/graphql/object/survey), [SurveyQuestion](https://developer.xurrent.com/graphql/object/surveyquestion), [SurveyResponse](https://developer.xurrent.com/graphql/object/surveyresponse) and [SurveyAnswer](https://developer.xurrent.com/graphql/object/surveyanswer). These new objects are also available for export/import.
- Updated: [Service](https://developer.xurrent.com/graphql/object/service) added the `survey` field.
- Updated: [ServiceFilter](https://developer.xurrent.com/graphql/input_object/servicefilter/) added the `survey` filter.

## July 24, 2021

- Updated: [ConfigurationItem](https://developer.xurrent.com/graphql/object/configurationitem) added the `purchaseValueCurrency` and `salvageValueCurrency` fields.
- Updated: Added the `costPerHourCurrency` field to [Person](https://developer.xurrent.com/graphql/object/person) and [SkillPool](https://developer.xurrent.com/graphql/object/skillpool).
- Updated: [Project](https://developer.xurrent.com/graphql/object/project) added the `valueCurrency` field.
- Updated: [TimeEntry](https://developer.xurrent.com/graphql/object/timeentry) added the `costCurrency` field.

## July 17, 2021

- Updated: [TaskTemplateFilter](https://developer.xurrent.com/graphql/input_object/tasktemplatefilter/) added the `assignee`, `team` and `skillPool` filters.
- Updated: [ProjectTaskTemplateFilter](https://developer.xurrent.com/graphql/input_object/projecttasktemplatefilter/) added the `assignee` filter.
- Updated: [InvoiceFilter](https://developer.xurrent.com/graphql/input_object/invoicefilter/) renamed the `type` filter into `ownerType`.
- Deprecated: [Service](https://developer.xurrent.com/graphql/object/service) deprecated the `provider` field in favor of `serviceProvider`.

## July 10, 2021

- Updated: Added the `resolutionDuration` field to [Workflow](https://developer.xurrent.com/graphql/object/workflow), [Problem](https://developer.xurrent.com/graphql/object/problem), [ProjectTask](https://developer.xurrent.com/graphql/object/projecttask), [Task](https://developer.xurrent.com/graphql/object/task), [Risk](https://developer.xurrent.com/graphql/object/risk), [Project](https://developer.xurrent.com/graphql/object/project) and [Request](https://developer.xurrent.com/graphql/object/request). The field has also been added as a column when exporting these models.

## July 3, 2021

- Updated: [AffectedSlaFilter](https://developer.xurrent.com/graphql/input_object/affectedslafilter/) added the `requestSource` filter.
- Updated: [RequestFilter](https://developer.xurrent.com/graphql/input_object/requestfilter/) added the `workflowStatus` filter.
- Updated: [TaskFilter](https://developer.xurrent.com/graphql/input_object/taskfilter/) added the `createdFromRequest` and `requesterOrganization` filters.

## June 19, 2021

- Updated: [Account](https://developer.xurrent.com/graphql/object/account) added `organization` field.
- Updated: [InvoiceOrderField](https://developer.xurrent.com/graphql/enum/invoiceorderfield) renamed `projectSubject` order to `invoiceableSubject`.
- Updated: [InvoiceFilter](https://developer.xurrent.com/graphql/input_object/invoicefilter) added the `workflow`, `contract`, `flsa`, `sla` and `type` filters.
- Updated: [Languages](https://developer.xurrent.com/graphql/scalar/language) added the Icelandic language.

## June 12, 2021

- Updated: [Note](https://developer.xurrent.com/graphql/object/note/) added `internal` & `account` fields, removed the `internalAccount` field.
- Updated: [ProjectTasks](https://developer.xurrent.com/graphql/object/projecttask/) added the Agile Board, Agile Board Column and Agile Board Column Position fields.

## June 5, 2021

- Updated: [RequestFilter](https://developer.xurrent.com/graphql/input_object/requestfilter/) add the `desiredCompletionAt` filter.
- Updated: [Knowledge Articles API](../../knowledge_articles.html) added support for non-inline attachments.

## May 29, 2021

- Updated: [PermissionRole](https://developer.xurrent.com/graphql/scalar/permissionrole/) added the `financial_manager` role.
- Updated: [RequestTemplateFilter](https://developer.xurrent.com/graphql/input_object/requesttemplatefilter/) add the `team` and `member` filters.
- Updated: [Tasks](https://developer.xurrent.com/graphql/object/task/) added the Agile Board, Agile Board Column and Agile Board Column Position fields.

## May 15, 2021

- Updated: [Problems](https://developer.xurrent.com/graphql/object/problem/) added the Agile Board, Agile Board Column and Agile Board Column Position fields.

## May 8, 2021

- Updated: The ‘Apps’ section for [Applications](../../applications.html) uses updated record names. ‘Integrations’ are now called [App Offerings](https://developer.xurrent.com/graphql/object/appoffering/) and ‘Integration Instances’ are now [App Instances](https://developer.xurrent.com/graphql/object/appinstance/). This name change was also performed for the REST API and import/export.

## May 1, 2021

- Added: [Teams API](../../teams.html) added the `agile_board` field.
- Updated: [Knowledge Articles API](../../knowledge_articles.html) increased size of `keywords` field to 2048 characters
- Updated: [Request Templates API](../../request_templates.html) increased size of `keywords` field to 2048 characters
- Updated: [Services API](../../services.html) increased size of `keywords` field to 2048 characters
- Updated: [ServiceLevelAgreementFilter](https://developer.xurrent.com/graphql/input_object/servicelevelagreementfilter/) added the `customerRep` and `serviceLevelManager` filters.
- Added: [Agile Board Columns API](../../agile_boards/columns.html) added the `remove_after` field.

## April 24, 2021

- Updated: [Workflow Templates API](../../workflow_templates/phases.html) added the `phases` collection.
- Updated: [Workflows API](../../workflows/phases.html) added the `phases` collection.
- Updated: [Tasks API](../../tasks.html) added the `phase` field.
- Updated: [Risks API](../../risks.html) added the `mitigation_target_at` field.
- Updated: [Applications](../../applications.html) added a section for Apps referencing the [App Builder Framework on Github](https://github.com/code4me/4me-app-builder-nodejs).

## April 17, 2021

- New (in beta-test, **subject to change without notice**): [Integrations](https://developer.xurrent.com/graphql/object/integration/). Also available in [REST API](https://developer.xurrent.com/v1/integrations/) and [import](https://developer.xurrent.com/v1/import/integrations).
- Updated: [OrganizationFilter](https://developer.xurrent.com/graphql/input_object/organizationfilter/) added the `businessUnit` filter.

## April 3, 2021

- Added: `rejectionCount` field to [Tasks](https://developer.xurrent.com/graphql/object/task/#rejectioncount).

## March 27, 2021

- Updated: [Requests](../../requests.html) added the Agile Board, Agile Board Column and Agile Board Column Position attributes.
- Added: `productCategory` field to [Product](https://developer.xurrent.com/graphql/object/product/#productcategory).
- Added: UI extension for [ProductCategory](https://developer.xurrent.com/graphql/object/productcategory/) and custom fields based on that to
 [Product](https://developer.xurrent.com/graphql/object/product/) (also to REST API’s [product\_categories](../../product_categories/index.html)
 and [products](../../products.html)). The product custom fields can also be used to filter products via
 [ProductCustomFilter](https://developer.xurrent.com/graphql/input_object/productcustomfilter/). Export/Import of products and product categories is
 extended with the new columns.

## March 20, 2021

- Updated: [AffectedSlaFilter](https://developer.xurrent.com/graphql/input_object/affectedslafilter/) added the `serviceOwner` filter.
- Updated: [ServiceFilter](https://developer.xurrent.com/graphql/input_object/servicefilter/) added the `serviceOwner` filter.
- Updated: [ServiceInstanceFilter](https://developer.xurrent.com/graphql/input_object/serviceinstancefilter/) added the `serviceOwner` filter.
- Updated: [ServiceLevelAgreementFilter](https://developer.xurrent.com/graphql/input_object/servicelevelagreementfilter/) added the `serviceOwner` filter.
- Updated: Time Entries [REST API](../../time_entries.html)
 and [GraphQL API](https://developer.xurrent.com/graphql/object/timeentry/) added the Service Level Agreement and Service Instance attributes.

## March 13, 2021

- New: [Agile Boards](../../agile_boards/index.html)
- New: [Agile Boards Import](../../import/agile_boards/index.html)

## February 27, 2021

- Updated: Out of Office Periods [Rest API](../../out_of_office_periods.html),
 [Import](../../import/out_of_office_periods/index.html) and
 [GraphQL API](https://developer.xurrent.com/graphql/object/outofofficeperiod/) added the Effort Class attribute.
- Updated: [ConfigurationItemFilter](https://developer.xurrent.com/graphql/input_object/configurationitemfilter/) added the `serialNr` and `ruleSet` filter.
- Updated: [ProductFilter](https://developer.xurrent.com/graphql/input_object/productfilter/) added the `ruleSet` filter.
- Added: [WebhookPolicyCreateResponse](https://developer.xurrent.com/graphql/object/webhookpolicycreateresponse/) the generated public key can now be retrieved, as `publicKeyPem`, when creating a webhook policy.
- Added [webhook policies](../../webhook_policies.html) to the REST API.
- Fixed: `name` filters in the GraphQL API now support values containing a comma (`,`), through use of the new [TextFilter](https://developer.xurrent.com/graphql/input_object/textfilter/).
- Updated: [UI Extension Javascript API](../../ui_extensions/js_api.html#populate-suggest-fields) - added a section to describe how to populate custom suggest fields.

## February 20, 2021

- Updated: [ConfigurationItemFilter](https://developer.xurrent.com/graphql/input_object/configurationitemfilter/) added the `systemID`, `assetID` and `poNr` filters.
- Updated: [CustomCollectionElementFilter](https://developer.xurrent.com/graphql/input_object/customcollectionelementfilter/) added the `reference` filter.

## February 13, 2021

- Updated: [TimesheetSetting](https://developer.xurrent.com/graphql/object/timesheetsetting/) new timesheet settings option `notifyOnIncomplete` to prevent Xurrent from sending notifications to people whose timesheet is incomplete.
- Updated: [TimeEntryFilter](https://developer.xurrent.com/graphql/input_object/timeentryfilter/) time entries can now be filtered based on whether they are marked as deleted.

## January 30, 2021

- Updated: [JIT Provisioning](../../jit_provisioning/openid_connect.html) added support for JIT provisioning when using the Open ID Connect protocol.
- Updated: [Reservations](../../reservations.html) The **deprecated** filters `active`, `upcoming` and `past` have been removed, as announced on October 24, 2020.
- Updated: [Out of Office Periods](../../out_of_office_periods.html) The **deprecated** filters `upcoming` and `past` have been removed, as announced on October 24, 2020.
- Updated: [OAuth Authorization Code Grant](../../oauth/authorization_code_grant.html) updated the OAuth Authorization Code Grant documentation.

## January 16, 2021

- Updated: [Webhooks](../../webhooks.html#verification) require verification before they become active.
- Updated: [Webhooks](../../webhooks.html#verifying-the-authenticity-of-a-webhook) Verifying the Authenticity of a Webhook.

## January 9, 2021

- New: [SCIM User Custom Fields Extension](../../scim/users.html#custom-fields-extension)

## December 19, 2020

- Updated: documentation for CustomFilters (e.g. [RequestCustomFilter](https://developer.xurrent.com/graphql/input_object/requestcustomfilter/)) added explicit description of how to handle “select” fields and general improvements.
- Updated: filters for objects with a name field (e.g. [TeamFilter](https://developer.xurrent.com/graphql/input_object/teamfilter/) and [PersonFilter](https://developer.xurrent.com/graphql/input_object/personfilter/)) now also allow offer a `name` filter.
- Updated: [PersonFilter](https://developer.xurrent.com/graphql/input_object/personfilter/) added the `authenticationID`, `employeeID`, `supportID` and `primaryEmail` filters.
- Updated: [ConfigurationItemFilter](https://developer.xurrent.com/graphql/input_object/configurationitemfilter/) added the `label` filter.
- Updated: [ServiceInstanceFilter](https://developer.xurrent.com/graphql/input_object/serviceinstancefilter/) and [ServiceFilter](https://developer.xurrent.com/graphql/input_object/servicefilter/) added the `firstLineTeam` filter.
- Updated: [ReservationOfferingFilter](https://developer.xurrent.com/graphql/input_object/reservationofferingfilter/) removed the (non-functional) `source` and `sourceID` filters.

## December 12, 2020

- Updated: [TeamView](https://developer.xurrent.com/graphql/enum/teamview/) added the `managed_by_me` and `coordinated_by_me` views.
- Updated: [TeamFilter](https://developer.xurrent.com/graphql/input_object/teamfilter/) added the `manager` and `coordinator` filters.

## December 5, 2020

- Updated: [TaskStatus](https://developer.xurrent.com/graphql/scalar/taskstatus/) documented the `waiting_for_customer` status.
- New: [OAuth Client Credentials Grant](../../oauth/client_credentials_grant.html) documented the OAuth Client Credentials Grant.
- Updated: [customCollectionCreate Mutation](https://developer.xurrent.com/graphql/mutation/customcollectioncreate/) allow custom elements to be created at same time as collection using `newCollectionElements` field.
- Updated: [ProjectTaskFilter](https://developer.xurrent.com/graphql/input_object/projecttaskfilter) add `template` filter.

## November 30, 2020

- New: [Attachments](../data_types.html#attachments) documented how to upload attachments.
- Updated: [Custom Collections](https://developer.xurrent.com/graphql/object/customcollection/) added the `picture_uri` field.
- Updated: [Custom Collection Elements](https://developer.xurrent.com/graphql/object/customcollectionelement/) added the `picture_uri` field.
- Updated: [Languages](https://developer.xurrent.com/graphql/scalar/language) added the Chinese (Traditional) language.

## November 14, 2020

- Updated: [OAuth 2.0](../../oauth.html) documented the Refresh Token request.
- New: [AffectedSlaFilter](https://developer.xurrent.com/graphql/input_object/affectedslafilter) added `businessUnit` filter.
- New: [WorkflowFilter](https://developer.xurrent.com/graphql/input_object/workflowfilter) added `requesterOrganization` filter.

## November 7, 2020

- Updated: [Language](https://developer.xurrent.com/graphql/scalar/language) added the Basque language.
- Updated: [TaskFilter](https://developer.xurrent.com/graphql/input_object/taskfilter) renamed `member`
 filter to `assignee`.
- New: [ProjectTaskFilter](https://developer.xurrent.com/graphql/input_object/projecttaskfilter) added
 `assignee` filter.

## October 24, 2020

- Updated: [Reservations](../../reservations.html) added the predefined filters `open` and `completed`.
 **Deprecated** the previous predefined filters `active`, `upcoming` and `past`. These will be removed on January 30, 2021.
- Updated: [Out of Office Periods](../../out_of_office_periods.html) added the predefined filters `open` and `completed`.
 **Deprecated** the previous predefined filters `upcoming` and `past`. These will be removed on January 30, 2021.

## October 10, 2020

- Updated: [Knowledge Articles](../../knowledge_articles.html) added the `archive_date` field.
- Updated: [Tasks](../../tasks.html) added the `skill_pool` field.
- Updated: [Task Templates](../../task_templates.html) added the `skill_pool` field.

## September 19, 2020

- Updated: [GraphQL API Service Quotas](https://developer.xurrent.com/graphql/#service-quotas).
- New: [Custom Collections](https://developer.xurrent.com/graphql/object/customcollection/).
- New: [Custom Collections Elements](https://developer.xurrent.com/graphql/object/customcollectionelement/).

## September 12, 2020

- New: [GraphQL API](https://developer.xurrent.com/graphql).

## September 5, 2020

- New: [Adding a note to an existing record based on Source and SourceID](../../requests/mail.html#adding-a-note-to-an-existing-record-based-on-source-and-sourceid).

## August 7, 2020

- Updated: [Authentication](../../index.html#authentication) Updated the “Authentication” paragraph on the use of OAuth tokens and X-Xurrent-Account, and prefering Personal Access Tokens over API Tokens. Added strong discouragements of continued use of API Tokens.

## August 2, 2020

- New: [OAuth 2.0](../../oauth.html)
- Updated: [Task Templates](../../task_templates.html) The `approvers` endpoint, which was deprecated on November 19, 2017, has been removed.

## July 28, 2020

- Updated: [Requests](../../requests.html) added the `task` field.

## July 25, 2020

- Updated: [Service Level Agreements](../../service_level_agreements.html) added the `use_knowledge_from_service_provider` field.

## July 19, 2020

- Updated: [Service Offerings](../../service_offerings/index.html) added the `response_target_..._in_days`
 and `resolution_target_..._in_days` fields.
- Updated: [Standard Service Requests](../../standard_service_requests/index.html) added the `response_target_in_days`
 and `resolution_target_in_days` fields.
- Updated: [Affected SLAs](../../affected_slas/index.html) added the `maximum_response_duration_in_days`
 and `maximum_resolution_duration_in_days` fields.
- Updated: [Task Templates](../../task_templates.html) added the `request_template` and `request_service_instance` fields.
- Updated: [Tasks](../../tasks.html) added the `request_template`, `request_service_instance` and `request` fields.

## July 12, 2020

- New: [Reservations](../../reservations.html)
- New: [Reservations Import](../../import/reservations/index.html)
- New: [Reservation Offerings](../../reservation_offerings/index.html)
- New: [Reservation Offerings Import](../../import/reservation_offerings/index.html)
- Updated: [Request](../../requests.html)
 - added the `reservation` category
 - added the `reservation` field
- Updated: [Request Template](../../request_templates.html)
 - added the `reservation` category
 - added the `reservation_offerings` field

## July 6, 2020

- Updated: [Service Offerings](../../service_offerings/index.html) added the `recovery_time_objective`
 and `recovery_point_objective` fields, and deprecated the fields `maximum_risk_of_data_loss`,
 `offline_backup_schedule`, and `restore_duration`.

## June 22, 2020

- Removed: [Contacts](../../people/contacts.html) removed `chat_hipchat` from list of
 valid values for the `label` field

## May 30, 2020

- Updated: The `planned_duration_in_minutes` and `planned_effort_in_minutes` fields in
 [Tasks](../../tasks.html),
 [Task Approvals](../../tasks/approvals.html),
 [Task Templates](../../task_templates.html),
 [Task Template Approvals](../../task_templates/approvals.html),
 [Project Tasks](../../project_tasks.html),
 [Project Task Approvals](../../project_tasks/assignments.html),
 [Project Task Templates](../../project_task_templates.html), and
 [Project Task Template Approvals](../../project_task_templates/assignments.html),
 which were deprecated on November 30, 2019, have now been *removed* from API responses and Exports,
 and they can *not* be used in automation rules and PDF designs anymore.
 Use the fields `planned_duration` and `planned_effort` instead.

## May 29, 2020

- Updated: [Authentication](https://developer.xurrent.com/v1#authentication) documented authentication using Personal Access Tokens.

## April 22, 2020

- Updated: [Configuration Items](../../configuration_items/index.html) changed the data type of the `rate` field to `integer`.
- Updated: [Products](../../products.html) changed the data type of the `rate` field to `integer`.

## April 5, 2020

- Updated: [Trusted Organizations Import](../../import/trusted_organizations/index.html)
 added `Organization Account` column.
- Updated: [Time Entries Import](../../import/time_entries.html)
 added `Effort Class ID` column.

## March 15, 2020

- New: [Webhooks](../../webhooks/events.html) added the following events:
 - `automation_rule`

## March 8, 2020

- Updated: [Broadcasts](../../broadcasts.html) added the `customers` field.
- New: [Broadcasts - Customers](../../broadcasts/customers/index.html) added the ability to list the customers linked to a broadcast.

## March 1, 2020

- New: [Trusted Organizations Import](../../import/trusted_organizations/index.html)
- Updated: [Releases](../../releases.html) added `custom_fields`, `ui_extension` and `attachments`.
- Updated: [UI Extensions](../../ui_extensions.html) added the `release` category.
- Updated: added `time_spent` and `time_spent_effort_class` to
 - [Requests](../../requests.html)
 - [Problems](../../problems.html)
 - [Tasks](../../tasks.html)
 - [Project Tasks](../../project_tasks.html)

## February 22, 2020

- New: [Risks](../../risks.html)
- New: [Risks Import](../../import/risks/index.html)
- New: [Risk Severities](../../risk_severities/index.html)
- New: [Risk Severities Import](../../import/risk_severities/index.html)
- New: [Projects - Risks](../../projects/risks/index.html) added the ability to list the risks of a project.
- New: [Services - Risks](../../services/risks/index.html) added the ability to list the risks of a service.
- New: [Organizations - Risks](../../organizations/risks/index.html) added the ability to list the risks of an organization.
- New: [Webhooks](../../webhooks/events.html) added the following events:
 - `risk.create`
 - `risk.update`
 - `risk.note-added`
 - `risk.status-changed`
 - `risk.manager-changed`
- Updated: [UI Extensions](https://developer.xurrent.com/v1/extensions/) added the `risk` category.
- Updated: [UI Extension Javascript API](../../ui_extensions/js_api.html) listed the functions that can be used to interact with Risk fields.
- New: [Automation Rules](../../automation_rules.html)
- Updated: [Request Templates](../../request_templates.html) added the `effort_class` field.

## February 15, 2020

- Updated: [UI Extension Javascript API](../../ui_extensions/js_api.html) it is now possible to make the Configuration items field of the Xurrent Specialist Interface required using `ITRP.field('asset').required()`.
- Updated: [Export](../../export.html) added clarifications to the section “Generating an export file”

## February 6, 2020

- Updated: [Text Formatting](../text_formatting.html) removed undocumented conversion of HTML entities.

 Until now, [HTML Entities](https://developer.mozilla.org/en-US/docs/Glossary/Entity)
 in rich text fields added via the API, import, or other integrations,
 were converted to the corresponding Unicode glyph when rendering the rich text field.
 However, this functionality was undocumented and has now been removed.
 That means that a text such as `&euro; 42` will now be rendered literally as `&euro; 42` instead of `€ 42`.

## January 31, 2020

- Updated: [Organizations](../../organizations.html) added the `financialID` field.
- Updated: [Time Entries](../../time_entries.html) added the `note_id` field.
- Updated: [Timesheet Settings](../../timesheet_settings/index.html) added the `require_note` field.

## January 29, 2020

- New: [Webhooks](../../webhooks/events.html) added the following events:
 - `out_of_office_period.create`
 - `out_of_office_period.update`
 - `out_of_office_period.delete`
- Updated: the payload in the body of [Webhook events](../../webhooks/events.html) for time entries and out of office periods contains additional fields.

## January 20, 2020

- New: [Webhooks](../../webhooks/events.html) added the following events:
 - `broadcast.create`
 - `broadcast.update`
 - `contract.create`
 - `contract.update`
 - `request.major-incident-status-changed`
 - `time_entry.create`
 - `time_entry.update`
 - `time_entry.delete`

## January 13, 2020

- Updated: [People - Contacts](../../people/contacts.html) added `chat_teams` to the
 list of values that can be used as Label of the contact details.

## November 30, 2019

- **Deprecated** the `planned_duration_in_minutes` and `planned_effort_in_minutes` fields in
 [Tasks](../../tasks.html),
 [Task Approvals](../../tasks/approvals.html),
 [Task Templates](../../task_templates.html),
 [Task Template Approvals](../../task_templates/approvals.html),
 [Project Tasks](../../project_tasks.html),
 [Project Task Approvals](../../project_tasks/assignments.html),
 [Project Task Templates](../../project_task_templates.html), and
 [Project Task Template Approvals](../../project_task_templates/assignments.html).
 Access the `planned_duration` and `planned_effort` fields instead.
 The `..._in_minutes` fields have been removed from the documentation.

 Until May 30, 2020, the `..._in_minutes` fields will still be included in API responses and Exports,
 and they can still be used in automation rules and PDF designs.
 These fields have the same value as `planned_duration` and `planned_effort`:
 both sets of fields report their value *in minutes*.
- New: [UI Extension Javascript API](../../ui_extensions/js_api.html)

## November 25, 2019

- New: [OpenID Connect](../../sso/openid_connect/index.html)
- Updated: [Single Sign-On](../../sso.html) and [SAML](../../sso/saml/index.html)

## November 18, 2019

- New: [Out of Office Periods](../../out_of_office_periods.html)
- New: [Out of Office Periods Import](../../import/out_of_office_periods/index.html)

## November 13, 2019

- Updated: [Workflows API](../../workflows.html) added the `planned_effort`, `actual_effort`, `remaining_effort` and `effort_indication` fields.

## November 5, 2019

- New: [Skill Pools](../../skill_pools/index.html)
- New: [Skill Pools Import](../../import/skill_pools/index.html)
- New: [Service Level Agreements - Skill Pools](../../service_level_agreements/skill_pools/index.html)
 added the ability to link skill pools to service level agreements whose coverage is set to `skill_pools`.
- New: [People - Skill Pools](../../people/skill_pools/index.html)
 added the ability to link skill pools to people.
- Updated: [Services API](../../services.html) added the `keywords` field.
- Updated: [Services Import](../../import/services/index.html) added the `Keywords` column.

## October 27, 2019

- New: [Requests API](../../requests.html) added the `major_incident_status` field.

## October 20, 2019

- New: [Knowledge Articles](../../knowledge_articles.html) added the `created_by` field.

## October 16, 2019

- New: [Workflow Types](../../workflow_types.html) feature added for maintaining custom workflow types.

## September 30, 2019

- Updated: [Workflow Templates API](../../workflow_templates.html) the `justification` field is now required for workflow templates that have request templates linked to them.

## September 9, 2019

- New: [Calendar Hours](../../calendars/calendar_hours/index.html) added the ability to edit the calendar hours of a calendar.
- New: [Time Entries Import](../../import/time_entries.html) added the ability to import time entries.

## August 26, 2019

- New: [Knowledge Articles - Service Instances API](../../knowledge_articles/service_instances.html) added the ability to link service instances to knowledge articles.

## July 29, 2019

- Updated: [People API](../../people.html) added the `auto_translation` and `do_not_translate_languages` fields.
- Updated: [People Import](../../import/people.html) added the `Auto Translation` and `Do Not Translate Languages` columns.
- Updated: [Knowledge Articles API](../../knowledge_articles.html) documented the new
 Knowledge Article statuses. Added the`internal_specialists`,
 `covered_specialists`, `key_contacts` and `end_users` fields. Changed the
 `service` field to be required.

## July 24, 2019

- Updated: [Project Tasks](../../project_tasks.html) added the `team` and `planned_effort_in_minutes` fields.
- Updated: [Project Task Templates](../../project_task_templates.html) added the `team` and `planned_effort_in_minutes` fields.

## July 8, 2019

- Updated: [Webhooks](../../webhooks.html) added the parameter `payload[note_id]` to the webhook contents.

## June 27, 2019

- Updated: [Advanced UI Extension Examples](../../ui_extensions/advanced_examples.html) added examples for manipulating rich text fields.

## June 11, 2019

- Updated: [People](../../people.html) added the `support_domain` predefined filter, which returns
 people registered in an account *without* including the people registered in the related directory account.

 The same predefined filter was also added to [Sites](../../sites.html) and [Organizations](../../organizations.html),
 The API calls `GET /v1/sites` and `GET /v1/organizations` currently do not return records from the
 related directory account. However, in the future this will be adjusted, to bring these API calls in line with
 `GET /v1/people` and the Sites and Organizations views in the Xurrent Service.

 It is therefore recommended to start using `GET /v1/sites/support_domain` and `GET /v1/organizations/support_domain`
 to prepare for this upcoming change.

## June 3, 2019

- Updated: [Requests API](../../requests.html) added the `no_reply` completion reason.
- Updated: [Workflows - Tasks API](../../workflows/tasks/index.html) respond with `404 Not Found` while workflow is being created.

## May 27, 2019

- Updated: [Advanced UI Extension Examples](../../ui_extensions/advanced_examples.html) **Deprecated** jQuery features
 that have been removed from jQuery 3. While these features will continue to be available in Xurrent for a limited time,
 UI Extensions that use them should be migrated as soon as possible.

 Refer to the official [jQuery Core 3.0 Upgrade Guide](https://jquery.com/upgrade-guide/3.0/) to get a full list
 of breaking changes.

 The Advanced UI Extension Examples have been rewritten so that they no longer use deprecated or removed jQuery features. In particular:

 - Replaced `.removeAttr('checked')` by `.prop('checked', false)`
 - Replaced `.change()` by `.trigger('change')`
 - Replaced `.change(function() ...)` by `.on('change', function() ...)`, and similarly for uses of the
 event shorthands `blur`, `focus`, `click`, `keydown`, and so on
 - Replaced `.bind(...)` by `.on(...)`

## May 27, 2019

- Updated: [Export API](../../export.html) added `satisfactions` to the type of records
 that can be exported.

## May 11, 2019

- Updated: [Time Entries](../../time_entries.html) documented the `cost` and `effort_class` fields.
- Updated: [Mail API](../../requests/mail.html) a reply to an email notification of a request (or problem/task/…)
 that has been completed more than 28 days ago, but which last note has been added no more than 28 days ago,
 now also results in a note being added to the existing request, instead of a new request being created.

## May 1, 2019

- Updated:
 [Tasks](../../tasks.html),
 [Task Approvals](../../tasks/approvals.html),
 [Task Templates](../../task_templates.html),
 [Task Template Approvals](../../task_templates/approvals.html),
 [Project Tasks](../../project_tasks.html),
 [Project Task Approvals](../../project_tasks/assignments.html),
 [Project Task Templates](../../project_task_templates.html),
 [Project Task Template Approvals](../../project_task_templates/assignments.html)
 added the `planned_duration_in_minutes` and `planned_effort_in_minutes` fields
 as a replacement for `planned_duration` and `planned_effort`.

 As the name indicates, `planned_duration_in_minutes` contains the planned duration *in minutes*,
 whereas the original `planned_duration` field contained the planned duration *in hours*.

 The maximum value of these fields is 600000 (= 10000 hours).
- **Deprecated** the `planned_duration` and `planned_effort` fields.
 Access the `..._in_minutes` fields instead.
 The `planned_duration` and `planned_effort` fields have been removed from the documentation.

 For a limited time, these fields will still be included in API responses and Exports
 and continue to report the planned duration / effort in hours, calculated as the planned duration / effort in minutes
 divided by 60, rounded *up* to the nearest hour.

## April 30, 2019

- Removed: [Timesheet Settings](../../timesheet_settings/index.html) the `track_cost_of_time_spent` field is now deprecated
 and has been removed from the documentation.
 For a limited time, the field will still be included in API responses and Exports with value `true`.

## April 29, 2019

- Updated: [UI Extensions](../../ui_extensions.html) added the `source` and `sourceID` fields.
- Updated: [Workflows](../../workflows.html) added support for archiving, trashing and restoring of Workflow records.
- Updated: [People](../../people.html) added support for archiving, trashing and restoring of Person records.
- Updated: [Problems](../../problems.html) added support for archiving, trashing and restoring of Problem records.
- Updated: [Releases](../../releases.html) added support for archiving, trashing and restoring of Release records.
- Updated: [Requests](../../requests.html) added support for archiving, trashing and restoring of Request records.
- Updated: [Time Entries](../../time_entries.html) added support for archiving, trashing and restoring of Time Entry records.

## April 2, 2019

- Updated: [Data Types](../data_types.html) documented the `time_zone` data type. It now accepts time zone values from the [Time Zone Database](https://www.iana.org/time-zones).

## March 27, 2019

- Updated: [Mail API](../../requests/mail.html) updated the default `source` field value from `"email"` to `"Email"`.
- Updated: [Events API](../../requests/events.html) updated the default `source` field value from `"event"` to `"Event"`.
- Updated: [Source and Source ID](../source.html) updated the default `source` field value from `"api"` to `"Xurrent API"`.

## March 4, 2019

- Updated: [Mail API](../../requests/mail.html) updated the Mail API rules with the new “Allow inbound email to generate new requests” and “Allow replies to be added as notes” Email Policy options.
- Updated: [Export API](https://developer.xurrent.com/v1/exports/) added `notes` to the list exportable types.

## February 26, 2019

- New: [Okta Verified Provisioning (SCIM) Certification](../../scim/okta/index.html)
- New: Defining multiple [Single Sign-On](../../sso.html#multiple-identity-providers) configurations
- Updated: [Replies to automatic notifications](../../requests/mail.html#replies-to-automatic-notifications) now generate new request if record has been in its final status for more than 28 days.

## February 5, 2019

- Updated: [Configuration Items](../../configuration_items/index.html) the `support_team` field is no longer required when status of CI equals ‘Removed’.
- Updated: [People](../../people.html) added the `employeeID` field.

## January 30, 2019

- Updated: [People](../../people.html) added the `authenticationID` field.
- Updated: [JIT End User Access Provisioning](../../jit_provisioning/saml.html) supports `authenticationID` attribute.

## January 8, 2019

- Updated: [JIT End User Access Provisioning](../../jit_provisioning/saml.html) supports `primary_email` attribute.

## January 5, 2019

- Updated: Renamed ‘States’ to [Predefined Filters](../filtering.html#predefined-filters) throughout the documentation.
 Moved the APIs listed under ‘List records relevant for API Users’ to the ‘Predefined filters’ paragraph.

## December 10, 2018

- New: [Email Templates Import](../../import/email_templates/index.html) added API for importing and exporting email templates.

## December 5, 2018

- Updated: `picture_uri` is writable and can be used to update the avatar image of [Holidays](../../holidays.html#fields), [Organizations](../../organizations.html#fields), [People](../../people.html#fields), [Product Categories](../../product_categories/index.html#fields), [Products](../../products.html#fields), [Service Categories](../../service_categories/index.html#fields), [Sites](../../sites.html#fields) and [Teams](../../teams.html#fields)

## November 24, 2018

- New: [Request Satisfaction](../../requests/satisfaction.html) added API for setting satisfaction or dissatisfaction with the manner in which a request has been handled.

## November 17, 2018

- Updated: [Broadcasts](../../broadcasts.html) added the `customers` visibility.

## November 13, 2018

- Updated: [Workflows](../../workflows.html) added the `failed` and `disruptive` completion reasons.
- Updated: [Releases](../../releases.html) added the `failed` and `disruptive` completion reasons.

## November 5, 2018

- Updated: [Service Categories](../../service_categories/index.html) added the ability to remove service categories.

## October 29, 2018

- Updated: [UI Extensions](../../ui_extensions/versions.html#fields) removed the `approval_status` field.
- Updated: [Broadcasts - Translations](../../broadcasts/translations/index.html) allow removal of translations via the API.
- Updated: [Knowledge Articles - Translations](../../knowledge_articles/translations/index.html) allow removal of translations via the API.

## October 9, 2018

- Updated: [Permissions](../../people/permissions.html#fields) added the `account_designer` and the `directory_designer` options for the `roles` field.

## September 29, 2018

- Updated: [Request Templates](../../request_templates.html) added the `keywords` field.
- New: [Webhooks](../../webhooks.html) added the `account_id` and `custom_url` fields.

## September 19, 2018

- New: [UI Extensions Import](../../import/ui_extensions/index.html) added documentation on importing UI extensions.
- New: [Export API](../../export.html) feature added for exporting UI extensions.

## September 11, 2018

- Updated: [Icons](../icons/index.html) updated the list of icons.
- Updated: [Workflows](../../workflows.html) the manager field can now be set for new workflows.
 The API user is still selected as the manager of a new workflow by default.
- Updated: [Product](../../products.html) if left empty, the name field of a new product is now automatically set
 to the values specified for the brand, model, productID (optional) and category fields.

## September 2, 2018

- Updated: [Requests](../../requests.html) added the `reopen_count` field.

## August 27, 2018

- Updated: [Requests](../../requests.html#list-requests-relevant-for-api-user) added the retrieval option `sla_accountability`.
- Updated: [Permissions](../../people/permissions.html#revoke-all-roles-from-a-person) added API for removing all roles from a person.
- Updated: [Workflows](../../workflows.html) documented the `being_created` status.

## August 12, 2018

- New: [Effort Classes](../../effort_classes.html)
- New: [Effort Classes Import](../../import/effort_classes/index.html)
- New: [Timesheet Settings - Effort Classes](../../timesheet_settings/effort_classes/index.html)
 added the ability to link effort classes to timesheet settings.
- Updated: [Timesheet Settings](../../timesheet_settings/index.html) added the `request_effort_class`, `task_effort_class`,
 `project_task_effort_class`, `problem_effort_class`, and `time_allocation_effort_class`
 fields.
- Updated: [Time Allocations](../../time_allocations/index.html),
 [Task Templates](../../task_templates.html), and
 [Project Task Templates](../../project_task_templates.html) added the `effort_class` field.
- Updated: [Rate Limiting](../../index.html#rate-limiting) added the `X-RateLimit-Reset` HTTP header field.
- New: [Rate Limit](../../rate_limit.html) API

## July 29, 2018

- Updated: [Requests](../../requests.html) added the `feedback` field.

## July 15, 2018

- Updated: [Tasks](../../tasks.html),
 [Project Tasks](../../project_tasks.html),
 [Task Templates](../../task_templates.html), and
 [Project Task Templates](../../project_task_templates.html) added the `work_hours_are_24x7` field.

## July 8, 2018

- New: the [Icons](../icons/index.html) page.
- New: [Archive](../../archive/index.html)
- New: [Trash](../../trash/index.html)

## July 1, 2018

- Updated: [Workflows](../../workflows.html),
 [Configuration Items](https://developer.xurrent.com/v1/cis/),
 [Contracts](../../contracts/index.html),
 [Organizations](../../organizations.html),
 [People](../../people.html),
 [Project Tasks](../../project_tasks.html),
 [Projects](../../projects/index.html),
 [Requests](../../requests.html),
 [Sites](../../sites.html), and
 [Tasks](../../tasks.html) added the `custom_fields` field as a replacement of `custom_data`.

 - Deprecated the `custom_data` field. Access the `custom_fields` field instead.
 The `custom_data` field has been removed from the documentation.
- Updated: added the `Custom Fields` column to the import/export of the above-mentioned record types.

 - Deprecated the `Custom Data` column. Use the `Custom Fields` column instead.
 The `Custom Data` column has been removed from the documentation.
- Updated: [People](../../people.html) added the `send_email_notifications` and `show_notification_popup` fields.

## June 5, 2018

- New: [Translations Import](../../import/translations/index.html) added documentation on importing translations.
- Updated: [Audit Entries](../../audit_entries.html) added the `created_by` field.
 Changed the `auditable` field and the references in the `workflows` field, so that they now contain the standard
 attributes in a [reference](../data_types.html#references).

 - Deprecated the `user` field. Access the `created_by` field instead. The `user` field has been removed from the documentation.
 - Deprecated the `display_name` attribute in the `auditable` and `workflows` field.
 Access the `name` or `subject` attribute instead, depending on the type of [reference](../data_types.html#references).

## May 17, 2018

- Updated: [CTI](../../cti/index.html) added the ability to specify the Request ID via the
 CTI interface

## May 5, 2018

- Updated: [Search API](../../search/index.html) added the ability to search for `ci` and
 `service-instance` records.

## April 19, 2018

- New: [SCIM Provisioning](../../scim.html) for automatic provisioning of user data.

## April 14, 2018

- Updated: [Notes](../../notes.html) added the state `public`

## April 9, 2018

- Updated: [Time Allocations - Organizations](../../time_allocations/organizations/index.html) added the ability to link organizations to a time allocation.

## March 19, 2018

- Updated: [Problems](../../problems.html) added the `custom_data` field and the `ui_extension` field.

## March 12, 2018

- Updated: [JIT End User Access Provisioning](../../jit_provisioning/saml.html) supports `first_name` and `last_name` attributes.

## March 9, 2018

- Updated: [Product](../../products.html) added the `productID` field.
- Updated: [Product Import](../../import/products.html) added the `Product ID` column.

## February 26, 2018

- Updated: [Export API](../../export.html) When the first column of a CSV export file is `ID`, the column header will now be
 enclosed in quotation marks, like this: `"ID"`. This makes it more convenient to open such files in Microsoft Excel,
 which might otherwise incorrectly assume that the file has the [SYLK](https://en.wikipedia.org/wiki/SYmbolic_LinK_(SYLK)) format.

## February 21, 2018

- Updated: [Workflows Import](../../import/workflows.html) added the `Release` column.

## February 18, 2018

- Updated: [Problems](../../problems.html) added the `knowledge_article` field.

## February 10, 2018

- Deprecated `X-ITRP-Account` header. Use [X-Xurrent-Account](../../index.html#multiple-accounts) instead.
- Deprecated `X-ITRP-Language` header. Use [X-Xurrent-Language](../../index.html#internationalization) instead.
- Deprecated `X-ITRP-Source` header. Use [X-Xurrent-Source](../source.html) instead.
- Deprecated `X-ITRP-Export` and `X-ITRP-ExportID` headers. Use [X-Xurrent-Export](../../export.html#downloading-an-export-file) resp. [X-Xurrent-ExportID](../../export.html#downloading-an-export-file) instead

## February 4, 2018

- Updated: [Search](../../search/index.html) added the ability to perform searches on behalf of someone else.
- Updated: [People - Configuration items](../../people/cis/index.html) added the ability to link configuration items to a person.
- Updated: [Time Entries](../../time_entries.html) changed the organization field from read-only to required.

## January 25, 2018

- Updated: [Request Template](../../request_templates.html) renamed the following fields: self\_service -> end\_users, service\_hierarchy\_browser -> specialists.
- Updated: [Request Template Import](../../import/request_templates.html) renamed the following columns: Self Service -> End Users, Service Hierarchy Browser -> Specialists.
- Updated: [Knowledge Article](../../knowledge_articles.html) added the keywords field.
- Updated: [Knowledge Article Import](../../import/knowledge_articles.html) added the Keywords column.

## January 19, 2018

- Updated: [Account](../../account.html) added the time\_format\_24h field.
- Updated: [People](../../people.html) added the work\_hours field.
- Updated: [People Import](../../import/people.html) added the Work Hours column.

## November 26, 2017

- New: [Invoices](../../invoices.html) added for creating and maintaining invoices for projects.
- New: [Invoices Import](../../import/invoices.html) making it possible to import invoices for projects.

## November 19, 2017

- New: [Task Templates - Approvals](../../task_templates/approvals.html) makes it possible to add, update and remove the approvers of a task template and to set the planned effort for each approver.
- Removed: Task Templates - Approvers is now deprecated and has been removed from the documentation. The ability to maintain a task template’s approvers has been replaced by [Task Templates - Approvals](../../task_templates/approvals.html).
- Updated: [Tasks](../../tasks.html) added the planned\_effort field for risk & impact and implementation tasks.
- Updated: [Task Approvals](../../tasks/approvals.html) added the planned\_effort field.
- Updated: [Task Templates](../../task_templates.html) added the planned\_effort, planned\_effort\_workflow\_manager, planned\_effort\_requester, planned\_effort\_requester\_business\_unit\_manager, planned\_effort\_requester\_manager and planned\_effort\_service\_owner fields.
- Updated: [Tasks Import](../../import/tasks.html) added the Planned Effort column.
- Updated: [Task Approvals Import](../../import/task_approvals/index.html) added the Planned Effort column.
- Updated: [Task Templates Import](../../import/task_templates.html) added the columns: Planned Effort Workflow Manager,Planned Effort Service Owner,Planned Effort Requester,Planned Effort Requester Manager,Planned Effort Requester Business Unit Manager.
- New: [Task Template Approvals Import](../../import/task_template_approvals/index.html) makes it possible to maintain the approvers and their planned effort for task templates using imports.
- Removed: [Task Templates Import](../../import/task_templates.html) removed the Approvers column. The approvers of task templates can now be imported using the new [Task Template Approvals Import](../../import/task_template_approvals/index.html).

## November 13, 2017

- New: [Search API](../../search/index.html) makes it possible to search through the most relevant Xurrent records for the API’s user.
- Updated: [Service Offerings](../../service_offerings/index.html) added the response\_target\_rfc, resolution\_target\_rfc, support\_hours\_rfc, response\_target\_rfi, resolution\_target\_rfi and support\_hours\_rfi fields.
- Updated: [Request Templates](../../request_templates.html) added the `copy_subject_to_requests` field.
- Updated: [Request Templates Import](../../import/request_templates.html) added the columns: Created At,Updated At,Copy Subject to Requests.
- Updated: [Knowledge Articles Import](../../import/knowledge_articles.html) added the columns: Created At,Updated At.
- Updated: [Workflow Templates Import](../../import/workflow_templates.html) added the columns: Created At,Updated At.
- Updated: [Task Templates Import](../../import/task_templates.html) added the columns: Created At,Updated At,PDF Design.
- Updated: [Project Templates Import](../../import/project_templates/index.html) added the columns: Created At,Updated At.
- Updated: [Project Task Templates Import](../../import/project_task_templates/index.html) added the columns: Created At,Updated At,PDF Design.
- Updated: [Project Task Template Assignments Import](../../import/project_task_template_assignments/index.html) added the columns: Created At,Updated At.

## November 05, 2017

- Updated: [Requests](../../requests.html) added the options `duplicate`, `rejected` and `declined` to the completion\_reason field.
- Updated: [Notes](../../notes.html) added the medium field with the options `default`, `email`, `system`, `redacted` and `automation`.

## October 23, 2017

- Updated: [Just-in-Time End User Access Provisioning](../../jit_provisioning/saml.html) added the attribute ‘jit’.

## September 30, 2017

- Updated: [Service Offerings Import](../../import/service_offerings/index.html) added the following columns to the import CSV file example: Response Target RFC,Resolution Target RFC,Support Hours RFC,Response Target RFI,Resolution Target RFI,Support Hours RFI

## September 02, 2017

- Updated: [Configuration Items Import](../../import/cis/index.html) added the Created At column and the Updated At column to the import CSV file example.
- Updated: [Import API](../../import.html) the import progress response now includes the URL of the import log when the import job has been completed successfully or with one or more unrecoverable errors.

## August 12, 2017

- Updated: [Service Level Agreements](../../service_level_agreements.html) the coverage field option `organizations_and_sites` has been added.
- Updated: [Service Level Agreements](../../service_level_agreements.html) the coverage field option `organization_and_descendants` has been renamed to `organizations_and_descendants` because multiple organizations can now be selected when this coverage option is selected.
- Updated: [Service Level Agreements - Sites](../../service_level_agreements/sites/index.html) feature extended so that it can also be used when the coverage field of an SLA is set to `organizations_and_sites`.
- Updated: [Service Level Agreements - Organizations](../../service_level_agreements/organizations/index.html) feature extended so that it can also be used when the coverage field of an SLA is set to `organizations_and_descendants` or `organizations_and_sites`.
- Removed: [Service Level Agreements](../../service_level_agreements.html) removed the field organization. The covered organizations of an SLA can now all be maintained using the [Service Level Agreements - Organizations](../../service_level_agreements/organizations/index.html) API.
- Updated: [Service Level Agreements Import](../../import/slas.html) the Coverage column option `organization_and_descendants` has been renamed to `organizations_and_descendants` because multiple organizations can now be selected when this coverage option is selected.

## July 30, 2017

- New: [Just-in-Time End User Access Provisioning](../../jit_provisioning/saml.html) allows a support organization’s [identity provider](https://en.wikipedia.org/wiki/Identity_provider) to take over the responsibility for registering and maintaining the organization’s end users in Xurrent.
- Updated: [Project Templates - Project Task Templates](../../project_templates/project_task_templates/index.html) added the states `enabled` and `disabled` to make it possible to retrieve only the enabled or disabled project task templates that are related to a specific project template.

## July 08, 2017

- Removed: [Organizations](../../organizations.html) replaced the ui\_extension\_id field with the ui\_extension field.
- Updated: [Contracts](../../contracts/index.html) added the custom\_data field and the ui\_extension field.
- Updated: [People](../../people.html) added the custom\_data field and the ui\_extension field.
- Updated: [Sites](../../sites.html) added the custom\_data field and the ui\_extension field.
- Updated: [UI Extensions](../../ui_extensions.html) added the category options `contract`, `person` and `site`.

## June 22, 2017

- Updated: [UI Extensions](../../ui_extensions/advanced_examples.html) improved the advanced examples for date selection restrictions.

## June 20, 2017

- Updated: [Project Tasks - Assignments](../../project_tasks/assignments.html) added the planned\_effort field.
- Updated: [Project Task Templates](../../project_task_templates.html) added the planned\_effort\_project\_manager, planned\_effort\_requester, planned\_effort\_requester\_business\_unit\_manager, planned\_effort\_requester\_manager and planned\_effort\_service\_owner fields.
- New: [Project Task Templates - Assignments](../../project_task_templates/assignments.html) added the ability to maintain the assignments of project task templates
- Removed: Project Task Templates - Assignees has been replaced by the new [Project Task Templates - Assignments](../../project_task_templates/assignments.html) API.
- Updated: [Project Task Assignments Import](../../import/project_task_assignments/index.html) added the Planned Effort column to the import CSV file example.
- Updated: [Project Task Templates Import](../../import/project_task_templates/index.html) removed the Assignees column and added the Planned Effort Project Manager, Planned Effort Service Owner, Planned Effort Requester, Planned Effort Requester Manager and Planned Effort Requester Business Unit Manager columns to the import CSV file example.
- New: [Project Task Template Assignments Import](../../import/project_task_template_assignments/index.html) added the ability to import project task template assignments. This replaces the Assignees column of the Project Task Template import CSV file and allows a planned effort to be specified for each assignee.

## June 05, 2017

- Updated: [Services](../../services.html) added the knowledge\_manager field.
- Updated: [Services Import](../../import/services/index.html) added the Knowledge Manager column to the import CSV file example.

## May 28, 2017

- Updated: [Requests Import](../../import/requests.html) added the Knowledge Article column to the import CSV file example.

## May 20, 2017

- New: [Organizations - Time Allocations](../../organizations/time_allocations/index.html) added the ability to maintain the relations between organizations and time allocations.
- Updated: [Products Import](../../import/products.html) added the Active CIs column to the import CSV file example.

## May 15, 2017

- Updated: [Account](../../account.html) added the strong\_privacy field.

## May 06, 2017

- Updated: [Requests](../../requests.html) added the addressed field.
- Updated: [UI Extensions](../../ui_extensions/advanced_examples.html) add several advanced examples of UI extensions with JavaScript code.
- Updated: [People - Permissions](../../people/permissions.html) features added to allow maintenance of people’s permissions.
- Removed: [People](../../people.html) the permissions field is now deprecated and has been removed from the documentation.

## April 30, 2017

- Updated: [People](../../people.html) added the vip field.
- Updated: [People Import](../../import/people.html) added the VIP column to the import CSV file example.
- Updated: [Request](../../requests.html) added the knowledge\_article field.
- Updated: [Knowledge Article](../../knowledge_articles.html) added the times\_applied field.
- New: [Knowledge Articles - Requests](../../knowledge_articles/requests/index.html) to retrieve the requests to which a knowledge article is linked.

## April 15, 2017

- Updated: [People - Contacts](../../people/contacts.html) added the chat field.

## March 28, 2017

- New: [Calendars](../../calendars/index.html#get-a-duration) added a feature for calculating the amount of active calendar time between a start and end moment.
- Updated: [Mail API](../../requests/mail.html#adding-a-note-to-an-existing-record) extended the ability to use a new email (as opposed to a reply to an automated email notification from Xurrent) to add a note to an existing request. This feature has been extended to existing problems, releases, workflows, workflow tasks, projects and project tasks.

## March 12, 2017

- Updated: [Requests](../../requests.html#list-requests-relevant-for-api-user) added the retrieval option `requested_by_or_for_me`.
- Updated: [Requests](../../requests.html#list-requests-relevant-for-api-user) added the retrieval option `requests_of_my_organization`.
- Updated: [Requests](../../requests.html#list-requests-relevant-for-api-user) added the retrieval option `assigned_to_my_team`.
- Updated: [Requests](../../requests.html#list-requests-relevant-for-api-user) added the retrieval option `assigned_to_me`.
- Updated: [Requests](../../requests.html#list-requests-relevant-for-api-user) added the retrieval option `waiting_for_me`.
- Updated: [Requests](../../requests.html#list-requests-relevant-for-api-user) added the retrieval option `problem_management_review`.
- Updated: [Knowledge Article](../../knowledge_articles.html#list-knowledge-articles-relevant-for-api-user) added the retrieval option `managed_by_me`.
- Updated: [Problems](../../problems.html#list-problems-relevant-for-api-user) added the retrieval option `managed_by_me`.
- Updated: [Problems](../../problems.html#list-problems-relevant-for-api-user) added the retrieval option `assigned_to_my_team`.
- Updated: [Problems](../../problems.html#list-problems-relevant-for-api-user) added the retrieval option `assigned_to_me`.
- Updated: [Releases](../../releases.html#list-releases-relevant-for-api-user) added the retrieval option `managed_by_me`.
- Updated: [Workflows](../../workflows.html#list-workflows-relevant-for-api-user) added the retrieval option `managed_by_me`.
- Updated: [Tasks](../../tasks.html#list-tasks-relevant-for-api-user) added the retrieval option `managed_by_me`.
- Updated: [Tasks](../../tasks.html#list-tasks-relevant-for-api-user) added the retrieval option `assigned_to_my_team`.
- Updated: [Tasks](../../tasks.html#list-tasks-relevant-for-api-user) added the retrieval option `assigned_to_me`.
- Updated: [Tasks](../../tasks.html#list-tasks-relevant-for-api-user) added the retrieval option `approval_by_me`.
- Updated: [Projects](../../projects/index.html#list-projects-relevant-for-api-user) added the retrieval option `managed_by_me`.
- Updated: [Project Tasks](../../project_tasks.html#list-project-tasks-relevant-for-api-user) added the retrieval option `managed_by_me`.
- Updated: [Project Tasks](../../project_tasks.html#list-project-tasks-relevant-for-api-user) added the retrieval option `assigned_to_me`.
- Updated: [Project Tasks](../../project_tasks.html#list-project-tasks-relevant-for-api-user) added the retrieval option `open_to_me`.
- Updated: [Products](../../products.html#list-products-relevant-for-api-user) added the retrieval option `supported_by_my_teams`.
- Updated: [Configuration Items](../../configuration_items/index.html#list-configuration-items-relevant-for-api-user) added the retrieval option `supported_by_my_teams`.
- Updated: [Organizations](../../organizations.html#list-organizations-relevant-for-api-user) added the retrieval option `managed_by_me`.

## February 19, 2017

- Updated: [Webhooks](../../webhooks.html) added the parameter `payload[audit_line_id]` to the webhook contents.
- Updated: [Webhooks](../../webhooks.html) ensured that the following parameters are included in the webhook contents whenever these fields have a value in the record that triggered the webhook event:
 - `payload[team][account][name]`
 - `payload[team][account][id]`
 - `payload[member][account][name]`
 - `payload[member][account][id]`

## February 07, 2017

- Updated: [Contracts](../../contracts/index.html) string length of name field limited to 128 characters.
- Updated: [First Line Support Agreements](../../first_line_support_agreements/index.html) string length of name field limited to 128 characters.
- Updated: [Project Task Templates](../../project_task_templates.html) string length of subject field limited to 190 characters.
- Updated: [Project Templates](../../project_templates/index.html) string length of subject field limited to 190 characters.
- Updated: [Service Categories](../../service_categories/index.html) string length of name field limited to 128 characters.
- Updated: [Task Templates](../../task_templates.html) string length of subject field limited to 190 characters.
- Updated: [UI Extensions](../../ui_extensions.html) string length of name field limited to 190 characters.

## January 20, 2017

- New: [Project Categories](../../project_categories/index.html) added for creating and maintaining the category options that can be selected for projects.
- New: [Project Risk Levels](../../project_risk_levels/index.html) added for creating and maintaining the risk options that can be selected for projects.
- New: [Project Task Templates](../../project_task_templates.html) added for creating and maintaining the templates that can be used to create project tasks.
- New: [Project Templates](../../project_templates/index.html) added for creating and maintaining the templates that can be used to add a set of project tasks to a project.
- New: [Project Tasks](../../project_tasks.html) added for creating and updating project tasks.
- New: [Project Templates](../../project_templates/index.html) added for creating and updating projects.
- New: [Project Categories Import](../../import/project_categories/index.html) added the ability to import the project categories.
- New: [Project Risk Levels Import](../../import/project_risk_levels/index.html) added the ability to import the project risk levels.
- New: [Project Task Templates Import](../../import/project_task_templates/index.html) added the ability to import the project task templates.
- New: [Project Templates Import](../../import/project_templates/index.html) added the ability to import the project templates.
- New: [Project Tasks Import](../../import/project_tasks/index.html) added the ability to import the project tasks.
- New: [Projects Import](../../import/projects.html) added the ability to import the projects.
- Updated: [UI Extensions](../../ui_extensions.html) added the category options `project` and `project_task_template`.

## January 15, 2017

- Updated: [Pagination](../pagination.html) limited the maximum number of records that can be retrieved as a single collection of pages to 100.000 records.

## December 23, 2016

- Updated: [Organizations](../../organizations.html) added the state `directory` for the retrieval of organizations from the directory account of the support domain account from which the data is requested.
- Updated: [People](../../people.html) added the state `directory` for the retrieval of people from the directory account of the support domain account from which the data is requested.
- Updated: [Sites](../../sites.html) added the state `directory` for the retrieval of sites from the directory account of the support domain account from which the data is requested.

## December 17, 2016

- Updated: [Mail API](../../requests/mail.html) described the ability to specify an inbound email address for teams.
- Updated: [Teams](../../teams.html) added the inbound\_email\_local\_part field.
- Updated: [Teams Import](../../import/teams/index.html) added the Inbound Email Local Part column to the import CSV file example.
- Updated: [Time Entries](../../time_entries.html) added the deleted field.

## December 03, 2016

- Updated: [Time Allocations](../../time_allocations/index.html) replaced the description\_required field with the description\_category field.
- Updated: [Time Allocations Import](../../import/time_allocations/index.html) replaced the Description Required column with the Description Category column.

## November 25, 2016

- New: [Knowledge Article](../../knowledge_articles.html) added for adding, updating and retrieving knowledge articles.
- Updated: [Webhooks](../../webhooks/events.html) added the description and mail\_exceptions\_to fields.

## November 05, 2016

- Updated: [Requests Import](../../import/requests.html) added the Problem, Workflow and Project columns to the import CSV file example.
- Updated: [Problems Import](../../import/problems.html) added the Project column to the import CSV file example.
- Updated: [Workflows Import](../../import/workflows.html) added the Project column to the import CSV file example.
- Updated: [People Roles Import](../../import/people_roles.html) added the Project Manager column to the import CSV file example.

## October 24, 2016

- Updated: [Request Templates](../../request_templates.html) added the urgent field.
- Updated: [Task Templates](../../task_templates.html) added the urgent field.

## October 09, 2016

- New: [Export API](../../export.html) feature added for exporting the time allocations of organizations.
- Removed: [Export API](../../export.html) the short URLs and system logs no longer get exported when the export type `all` is specified.

## September 24, 2016

- Updated: [Mail API](../../requests/mail.html) added the `markdown` parameter. This parameter can be included to indicate that Markdown is used in the body of the email to define how the text for the Note field is to be formatted.

## September 14, 2016

- New: [Text Formatting](../text_formatting.html) described the formatting options for rich text fields.

## September 12, 2016

- New: [Organizations Time Allocations Import](../../import/organizations_time_allocations/index.html) added the ability to import the links between organizations and time allocations.
- Updated: [Broadcasts](../../broadcasts.html) added the option `members_of_teams` for the visible\_for field. Also added the related teams field and ‘[Broadcasts - Teams API](../../broadcasts/teams/index.html)’

## August 22, 2016

- Updated: [Products](../../products.html) added the disabled field.

## August 14, 2016

- Removed: Support Efforts API has been replaced by the [Time Entries API](../../time_entries.html)

## August 06, 2016

- Updated: [Mail API](../../requests/mail.html) adjusted the rule that determines the default value for the team field of a new request. Now, when the new request is to be related to a service instance, the Support Team of this service instance also gets selected by default when the sender of the email is a member of the First Line Team or the Support Team of this service instance.
- Updated: [Events API](../../requests/events.html) adjusted the rule that determines the default value for the team field of a new request. Now, when the new request is to be related to a service instance, the Support Team of this service instance also gets selected by default when the current user is a member of the First Line Team or the Support Team of this service instance.

## July 16, 2016

- Updated: [Mail API](../../requests/mail.html) added a rule that allows a person to send an email for the generation of a new request (with or without parameters) to any Xurrent account of which this person has the Specialist role.
- Updated: [Tasks Import](../../import/tasks.html) removed the Fixed Start column from the import CSV file example.

## July 02, 2016

- Updated: [Workflows](../../workflows.html) added the manager field to the collection fields and enabled sorting on this field.

## June 10, 2016

- Updated: [Time Allocations](../../time_allocations/index.html) added the description\_required field.
- Updated: [Time Allocations Import](../../import/time_allocations/index.html) added the Description Required column.
- Updated: [Time Entries](../../time_entries.html) added the description field.
- Updated: [Requests](../../requests.html) added the first\_line\_team and standard\_service\_request fields.

## May 22, 2016

- Updated: [Timesheet Settings](../../timesheet_settings/index.html) replaced the allow\_overtime field with the allow\_workday\_overtime and allow\_workweek\_overtime fields.
- Updated: [Timesheet Settings Import](../../import/timesheet_settings.html) replaced the Allow Overtime column with the Allow Workday Overtime and Allow Workweek Overtime columns.

## May 14, 2016

- Updated: [Tasks Import](../../import/tasks.html) added the Service Instances and Configuration Items columns to the import CSV file example.

## April 26, 2016

- Updated: [Requests](../../requests.html) added the `requester_resolution_target_at` field.
- Updated: [Time Entries](../../time_entries.html) added the `correction` field.

## April 16, 2016

- Updated: [Requests](../../requests.html) added the `assignment_count` field.
- Updated: [Mail API](../../requests/mail.html) added a rule that limits updates of existing requests by incoming email without a reference in the mail header to within 28 days of their completion.
- Updated: [Filtering](../filtering.html) extended the filtering capabilities to less than, less than or equal to, greater than and greater than or equal to.

## April 12, 2016

- Updated: [Events API](../../requests/events.html) added the parameter support\_domain for users who are registered in a directory account.

## April 11, 2016

- Updated: [Mail API](../../requests/mail.html) added the section ‘Adding a note to an existing request’.

## April 10, 2016

- New: [Timesheets](../../timesheets/index.html) feature added for retrieving people’s timesheets.
- Updated: [Time Entries](../../time_entries.html) feature added for removing a time.

## April 02, 2016

- New: [Time Allocations](../../time_allocations/index.html) feature added for making allocations available for people to register time against.
- New: [Time Entries](../../time_entries.html) feature added for registering time.
- Updated: [Requests](../../requests.html) added the created\_by field.

## March 26, 2016

- New: [Timesheet Settings](../../timesheet_settings/index.html) feature added for defining the settings for people’s timesheets.

## March 19, 2016

- Updated: [Requests](../../requests.html) added the organization field.

## March 08, 2016

- Updated: [SLA](../../service_level_agreements.html) added the coverage option `organization_and_descendants` and the organization field.

## February 29, 2016

- Updated: [Problem](../../problems.html) added the waiting\_until field.
- Updated: [Tasks](../../tasks.html) added the waiting\_until field.
- Updated: [Problems Import](../../import/problems.html) added the Waiting Until column to the import CSV file example.
- Updated: [Tasks Import](../../import/tasks.html) added the Waiting Until column to the import CSV file example.

## February 17, 2016

- Updated: [Broadcasts](../../broadcasts.html) added the option `covered_for_any` for the visible\_for field.

## February 12, 2016

- Updated: [Task Templates](../../task_templates.html) added the instructions field.
- Updated: [Task Templates](../../task_templates.html) added the ui\_extension field.
- Updated: [Tasks](../../tasks.html) replaced the Initial note field with the instructions field.
- Updated: [Tasks](../../tasks.html) added the custom\_data field.

## February 05, 2016

- Updated: [Organization](../../organizations.html) added the substitute field.

## January 07, 2016

- Updated: [People - CI Coverages](../../people/ci_coverages.html) has replaced People - Available CI.

## December 21, 2015

- Updated: [Tasks - Predecessors](../../tasks.html) feature added to make it possible to add, update or remove a task’s predecessors.
- Updated: [Tasks - Successors](../../tasks.html) feature added to make it possible to add, update or remove a task’s successors.
- Renamed: [Task Templates](../../task_templates/workflow_templates.html) `task_template_parents` has become `workflow_templates`.

## December 07, 2015

- New: [Short URLs](../../short_urls/index.html) feature added for preparing short URLs for QR codes or NFC tags or simply for shortening long URLs.

## November 17, 2015

- Updated: [Webhooks](../../webhooks.html) added the parameter `payload[previous_status]` to the payload of ‘status-changed’ events.

## November 06, 2015

- New: [Account](../../account.html) feature added for retrieving account, billable usage and billable users data.

## November 01, 2015

- New: [Webhooks](../../webhooks.html) added ‘status-changed’ events for requests, problems, workflows and tasks.

## October 11, 2015

- New: [Export API](../../export.html) feature added for exporting the system logs.

## September 16, 2015

- New: [Product Categories](../../product_categories/index.html) feature added for maintaining product categories.
- Updated: [Products](../../products.html#fields) added the rule\_set field.
- Updated: [Configuration Items](../../configuration_items/index.html#fields) added the rule\_set field.

## September 09, 2015

- Updated: [Filtering](../filtering.html#states) extended the States feature to related records
- Updated: [Notes](../../notes.html) added the state `internal`
- Updated: [Workflows](../../workflows.html) added the release field.

## August 26, 2015

- Updated: [Requests](../../requests.html) added the desired\_completion\_at field.
- Updated: [Affected SLAs](../../affected_slas/index.html) added the desired\_completion\_at and the next\_target\_at fields.

## August 17, 2015

- Updated: [Events API](../../requests/events.html) extended the feature that dictates the default value for the member and status fields.
- Updated: [Mail API](../../requests/mail.html) extended the feature that dictates the default value for the member and status fields.

## August 10, 2015

- Updated: [Requests](../../requests.html) added the waiting\_until field.
- Updated: [Events API](../../requests/events.html) added the waiting\_until parameter.
- Updated: [Mail API](../../requests/mail.html) added the waiting\_until parameter.
- Updated: [Requests Import](../../import/requests.html) added the Waiting Until column to the import CSV file example.

## July 30, 2015

- Updated: [Organizations Import](../../import/organizations/index.html) added the UI Extension and Custom Data columns to the import CSV file example.

## July 26, 2015

- Updated: [Computer Telephony Integration (CTI)](../../cti/index.html) number matching extended beyond telephone numbers to support\_id field values.

## May 01, 2015

- Updated: [Configuration Items - CI Relations](../../configuration_items/ci_relations/index.html) feature extended by allowing configuration items of all product categories (with the exception of software license certificates) to have multiple parent CI relations.

## April 11, 2015

- Updated: [Tasks - Approvals](../../tasks/approvals.html) feature extended to make it possible to add, update or remove a task’s approval.
- Updated: [Service Offerings - Standard Service Requests](../../service_offerings/standard_service_requests/index.html) feature extended to make it possible to add, update or remove a service offering’s standard service request.
- Updated: [Configuration Items - CI Relations](../../configuration_items/ci_relations/index.html) feature extended to make it possible to add, update or remove a configuration item’s CI relation.
- Updated: [Organizations - Addresses](../../organizations/addresses/index.html) feature extended to make it possible to add, update or remove an organization’s address.
- Updated: [Organizations - Contacts](../../organizations/contacts/index.html) feature extended to make it possible to add, update or remove an organization’s contact.
- Updated: [People - Addresses](../../people/addresses.html) feature extended to make it possible to add, update or remove a person’s address.
- Updated: [People - Contacts](../../people/contacts.html) feature extended to make it possible to add, update or remove a person’s contact.

## December 14, 2014

- Updated: [Mail API - Event Matching](../../requests/mail.html#event-matching) feature and [Events API - Event Matching](../../requests/events.html#event-matching) feature now take into account the requested\_for parameter and is limited to requests generated over the past 24 hours.

## November 26, 2014

- Updated: [Task](../../tasks.html) feature updated to include the ID of the workflow when retrieving, adding and updating a task.
- Updated: [Requests - Configuration Items](../../requests/cis/index.html) feature extended to make it possible for a configuration item to be added to, or removed from, a request.
- Updated: [Problems - Configuration Items](../../problems/cis/index.html) feature extended to make it possible for a configuration item to be added to, or removed from, a problem.
- Updated: [Problems - Requests](../../problems/requests/index.html) feature extended to make it possible for a request to be added to, or removed from, a problem.
- Updated: [Problems - Service Instances](../../problems/service_instances/index.html) feature extended to make it possible for a service instance to be added to, or removed from, a problem.
- Updated: [Releases - Workflows](../../releases/workflows.html) feature extended to make it possible for a workflow to be added to, or removed from, a release.
- Updated: [Workflows - Problems](../../workflows/problems/index.html) feature extended to make it possible for a problem to be added to, or removed from, a workflow.
- Updated: [Workflows - Requests](../../workflows/requests/index.html) feature extended to make it possible for a request to be added to, or removed from, a workflow.
- Updated: [Tasks - Configuration Items](../../tasks/cis/index.html) feature extended to make it possible for a configuration item to be added to, or removed from, a task.
- Updated: [Tasks - Service Instances](../../tasks/service_instances/index.html) feature extended to make it possible for a service instance to be added to, or removed from, a task.
- Updated: [Workflow Templates - Task Templates](../../workflow_templates/task_templates/index.html) feature extended to make it possible for a task template to be added to, or removed from, a workflow template.
- Updated: [Task Templates - Approvers](https://developer.xurrent.com/v1/task_templates/approvers/) feature extended to make it possible for an approver to be added to, or removed from, a task template.
- Updated: [Task Templates - Configuration Items](../../task_templates/cis/index.html) feature extended to make it possible for a configuration item to be added to, or removed from, a task template.
- Updated: [Task Templates - Service Instances](../../task_templates/service_instances/index.html) feature extended to make it possible for a service instance to be added to, or removed from, a task template.
- Updated: [Service Instances - Configuration Items](../../service_instances/cis/index.html) feature extended to make it possible for a configuration item to be added to, or removed from, a service instance.
- Updated: [Service Level Agreements - Organizations](../../service_level_agreements/organizations/index.html) feature extended to make it possible for an organization to be added to, or removed from, a service level agreement.
- Updated: [Service Level Agreements - People](../../service_level_agreements/people/index.html) feature extended to make it possible for a person to be added to, or removed from, a service level agreement.
- Updated: [Service Level Agreements - Sites](../../service_level_agreements/sites/index.html) feature extended to make it possible for a site to be added to, or removed from, a service level agreement.
- Updated: [Configuration Items - Contracts](../../configuration_items/contracts/index.html) feature extended to make it possible for a contract to be added to, or removed from, a configuration item.
- Updated: [Configuration Items - Service Instances](../../configuration_items/service_instances/index.html) feature extended to make it possible for a service instance to be added to, or removed from, a configuration item.
- Updated: [Configuration Items - Users](../../configuration_items/users/index.html) feature extended to make it possible for a user to be added to, or removed from, a configuration item.
- Updated: [Contracts - Configuration Items](../../contracts/cis/index.html) feature extended to make it possible for a configuration item to be added to, or removed from, a contract.
- Updated: [Teams - Members](../../teams/members/index.html) feature extended to make it possible for a member to be added to, or removed from, a team.
- Updated: [People - Teams](../../people/teams/index.html) feature extended to make it possible for a team to be added to, or removed from, a person.
- Updated: [Broadcasts - Service Instances](../../broadcasts/service_instances/index.html) feature extended to make it possible for a service instance to be added to, or removed from, a broadcast.
- Updated: [Calendars - Holidays](../../calendars/holidays/index.html) feature extended to make it possible for a holiday to be added to, or removed from, a calendar.
- Updated: [Holidays - Calendars](../../holidays/calendars/index.html) feature extended to make it possible for a calendar to be added to, or removed from, a holiday.
- Updated: [Service Categories - Services](../../service_categories/services/index.html) feature extended to make it possible for a service to be added to, or removed from, a service category.

## September 07, 2014

- New: [Tasks - Approvals](../../tasks/approvals.html) feature added for linking multiple approvers to a task.
- New: [Task Templates - Approvers](https://developer.xurrent.com/v1/task_templates/approvers/) feature added for linking multiple approvers to a task template.
- Updated: [Request Templates](../../request_templates.html) feature extended with the new `instructions` field.
- Renamed: [Request Templates](../../request_templates.html) the field `instructions` was renamed to `registration_hints`.

## June 08, 2014

- Updated: [People - Permissions](../../people/permissions.html) feature extended with the `key contact` role.

## June 01, 2014

- New: [Broadcasts](../../broadcasts.html) feature added for adding, updating and retrieving broadcasts.

## March 20, 2014

- Updated: [Requests](../../requests.html) feature added for retrieving the `template` field value of requests.
- Updated: [Workflows](../../workflows.html) feature added for retrieving the `template` field value of workflows.
- Updated: [Tasks](../../tasks.html) feature added for retrieving the `template` field value of tasks.
- New: [Tasks of Workflows](../../workflows/tasks/index.html) feature added for retrieving all tasks of a workflow.

## March 06, 2014

- Updated: [Task Templates Import](../../import/task_templates.html) added the `Copy notes to workflow` column to task templates import files.

## February 28, 2014

- Updated: [Requests](../../requests.html) feature added for retrieving the `urgent` field value of requests.
- Updated: [Requests Import](../../import/requests.html) added the `Urgent` column to requests import files.
- Updated: [Problems](../../problems.html) feature added for retrieving the `urgent` field value of problems.
- Updated: [Problems Import](../../import/problems.html) added the `Urgent` column to problems import files.
- Updated: [Tasks](../../tasks.html) feature added for retrieving the `urgent` field value of tasks.
- Updated: [Tasks Import](../../import/tasks.html) added the `Urgent` column to tasks import files.

## February 20, 2014

- Updated: [Requests Import](../../import/requests.html) added the `Reviewed` column to requests import files.

## February 13, 2014

- Updated: [Configuration Item](../../configuration_items/index.html) updated the description for the `product` field as it is now possible to update its value.

## January 28, 2014

- New: [Service Category](../../service_categories/index.html) added the Service Categories API.
- New: [Service Categories Import](../../import/service_categories/index.html) feature added for uploading batches of service categories.
- New: [Export API](../../export.html) feature added for downloading batches of service categories.

## September 09, 2013

- Updated: [Webhooks](../../webhooks.html#webhook-contents) added payload parameters to the Webhook contents.
- New: [People](../../people.html#using-a-phone-number-to-get-a-person) feature added for retrieving people data using telephone numbers.

## August 19, 2013

- New: [Export API](../../export.html) feature added for downloading batches of affected SLAs and support efforts.

## August 14, 2013

- New: [First Line Support Agreements Import](../../import/first_line_support_agreements/index.html) feature added for uploading batches of first line support agreements.
- New: [Export API](../../export.html) feature added for downloading batches of first line support agreements.

## July 15, 2013

- New: [Workflow Templates Import](../../import/workflow_templates.html) feature added for uploading batches of workflow templates.
- New: [Export API](../../export.html) feature added for downloading batches of workflow templates.

## June 10, 2013

- New: [Export API](../../export.html) feature added for downloading batches of specific record types.
- New: [Releases Import](../../import/releases.html) feature added for uploading batches of releases.
- New: [Standard Service Request Import](../../import/standard_service_requests/index.html) feature added for uploading batches of standard service requests.

## October 19, 2012

- New: [Import API](../../import.html) feature added for uploading batches of specific record types.

## March 15, 2012

- New: [My Inbox](../../people/me/index.html#my-inbox)
- New: [My Team’s Inbox](../../people/me/index.html#my-teams-inbox)
- New: [Task Templates](../../task_templates.html#fields) added the assign\_to\_requester\_manager field.
- New: [Workflow Templates](../../workflow_templates.html#recurrence) added the recurrence fields
- Renamed: [Task Templates](../../task_templates.html#fields) the assign\_to\_manager field was renamed to `assign_to_workflow_manager`.

## December 25, 2011

First version of API released.
