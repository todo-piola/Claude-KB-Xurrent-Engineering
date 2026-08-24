# App Offering Automation Rules Import

App offering automation rules can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a app offering automation rules import file can be found in [App Offering Automation Rules API - Fields](../../app_offering_automation_rules/index.html#fields).

## CSV Example

```
"ID",Created At,Updated At,App Offering,App Offering ID,Model,Name,Position,Description,Trigger,Expressions,Condition,Actions
1,2021-04-13T04:19:50-05:00,2021-04-13T04:19:50-05:00,note-dispatcher,1,Request,Trigger webhook for each note added,1,,on note added,"text: notes[last].text
url: rule_app_instance.custom_fields.url",true,a1: call webhook '{app_offering_webhook}' with payload 'text url'
2,2021-04-13T04:20:25-05:00,2021-04-13T04:20:25-05:00,typeform,2,Request,Ask customer to complete survey,1,,on note added,"completed: status = completed
was_not_completed: status_was != completed
url: rule_app_instance.custom_fields.form_url",completed and was_not_completed,a1: add note 'Please complete our [survey at: {{url}}]({{url}})'
```

[download CSV](https://developer.xurrent.com/csv/app_offering_automation_rules.csv)
