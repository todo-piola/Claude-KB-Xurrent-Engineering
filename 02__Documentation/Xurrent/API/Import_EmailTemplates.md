# Email Templates Import

Email Templates can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8)
or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded
[comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values)
or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of an
Email Templates import file can be found in the [Fields](index.html#fields) section.

## CSV Example

```
Trigger,Disabled,Subject,Body,Email Design,Created At,Updated At
watchlist/item_updated,0,{{watchlist_item_record_type}} {{watchlist_item_title}},"Dear {{recipient_name}},

The following has been updated by {{updated_by_name}}:

{{watchlist_item_record_type}} {{watchlist_item_title}}

{{note_text}}

{{watchlist_item_link}}

You received this notification because you are watching {{watchlist_title}}.
[Click here]({{remove_from_watchlist_link}}) to remove it from your watchlist.",Default,2018-12-07T14:34:45-06:00,2018-12-07T14:34:45-06:00
mass_update/finished,0,Mass update of {{count}} {{records}} finished,"Dear {{recipient_name}},

The mass update of {{count}} {{records}} has been finished.

{{error_message}}
Summary: {{summary}}
Log file: {{log_file_link}}",Default,2018-12-07T14:34:45-06:00,2018-12-07T14:34:45-06:00
```

[download CSV](https://developer.xurrent.com/csv/email_templates.csv)

## Fields

trigger
: *Required* **[string](../../general/data_types.html)** —
 The trigger to generate the email notification. Valid values are:

 - `user/new_user`: New User
 - `user/password_changed`: Password Changed
 - `user/primary_email_changed`: Primary Email Changed
 - `user/get_access`: Get Access
 - `user/email_unknown`: Email Unknown
 - `user/email_rejected`: Email Rejected
 - `user/email_verification`: Email Verification
 - `user/email_verified`: Email Verified
 - `user/tfa_enable`: Enable Two-Factor Authentication
 - `user/tfa_enabled`: Enabled Two-Factor Authentication
 - `user/tfa_disabled`: Disabled Two-Factor Authentication
 - `user/tfa_recovery_code_used`: Two-Factor Authentication Recovery Code Used
 - `request/new_request_requested_by`: New Request
 - `request/new_request_requested_for`: New Request for Someone Else
 - `request/waiting_for_customer`: Request Set to Waiting for Customer
 - `request/desired_completion`: Desired Completion Set for Request
 - `request/completed`: Request Set to Completed
 - `request/team_assignment`: Request Assigned to Team
 - `request/member_assignment`: Request Assigned to Member
 - `request/member_reassignment`: Request Assignment Changed
 - `request/new_note`: Note Added to Request
 - `request/requester_dissatisfied`: Requester Dissatisfied
 - `problem/manager_changed`: Problem Manager Changed
 - `problem/team_assignment`: Problem Assigned to Team
 - `problem/member_assignment`: Problem Assigned to Member
 - `problem/member_reassignment`: Problem Assignment Changed
 - `problem/solved`: Problem Set to Solved
 - `problem/new_note`: Note Added to Problem
 - `release/workflow_added`: Workflow Added to Release
 - `release/workflow_removed`: Workflow Removed from Release
 - `release/progress_halted`: Release Set to Progress Halted
 - `release/manager_changed`: Release Manager Changed
 - `release/new_note`: Note Added to Release
 - `workflow/new_workflow`: New Workflow
 - `workflow/progress_halted`: Workflow Set to Progress Halted
 - `workflow/manager_changed`: Workflow Manager Changed
 - `workflow/new_note`: Note Added to Workflow
 - `task/team_assignment`: Task Assigned to Team
 - `task/member_assignment`: Task Assigned to Member
 - `task/approver_assignment`: Task Assigned to Approver
 - `task/member_reassignment`: Task Assignment Changed
 - `task/new_note`: Note Added to Task
 - `project/new_project`: New Project
 - `project/progress_halted`: Project Set to Progress Halted
 - `project/manager_changed`: Project Manager Changed
 - `project/new_note`: Note Added to Project
 - `project_task/assignment`: Project Task Assignment
 - `project_task/approver_assignment`: Project Task Approver Assignment
 - `project_task/reassignment`: Project Task Assignment Changed
 - `project_task/new_note`: Note Added to Project Task
 - `project_task/milestone_reached`: Milestone Reached
 - `project_task/milestone_missed`: Milestone Missed
 - `sla/activated`: SLA Set to Active
 - `sla/expired`: SLA Set to Expired
 - `flsa/activated`: First Line Support Agreement Set to Active
 - `flsa/expired`: First Line Support Agreement Set to Expired
 - `contract/activated`: Contract Set to Active
 - `contract/expired`: Contract Set to Expired
 - `agreement/upcoming_notice`: Upcoming Notice Date for Agreement
 - `agreement/upcoming_expiry`: Upcoming Expiry Date for Agreement
 - `timesheet/past_week_incomplete`: Past Week Incomplete
 - `watchlist/item_updated`: Watchlist Item Updated
 - `mass_update/finished`: Mass Update Finished

disabled
: *Optional* **[boolean](../../general/data_types.html)**, default: `false` —
 The Disabled box is checked when the email notifications that are based on the
 email template may not be generated.

email\_design
: *Required* **[reference](../../general/data_types.html#references) to Email Design** —
 The Email design field is used to select the email design that is to be applied
 to any email notifications that are generated based on the email template. In
 Edit mode, this field is available only when two or more email designs are
 available.

subject
: *Required* **[string](../../general/data_types.html) (max 255)** —
 The Subject field is used to specify the subject of email notifications that are
 generated based on the email template. Depending on the type of record for which
 the email is generated, different fields of this record (or related data) can be
 included in the Subject field.

body
: *Required* **[text](../../general/data_types.html)** —
 The Body field is used to specify the text that needs to be presented in the
 body of email notifications that are generated based on the email template.
 Depending on the type of record for which the email is generated, different
 fields of this record (or related data) can be included in the Body field.

created\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time at which the email template was created.

updated\_at
: *Readonly* **[datetime](../../general/data_types.html)** — The date and time of the last update of the email template. If the email template has no updates it contains the `created_at` value.
