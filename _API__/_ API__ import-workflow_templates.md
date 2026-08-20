# Workflow Templates Import

Workflow Templates can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Workflow Templates import file can be found in [Workflow Templates API - Fields](../../workflow_templates.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Subject,Instructions,Note,Service,Category,Type,Justification,UI Extension,Task Templates,Workflow,Recurrence - Disabled,Recurrence - Time Zone,Recurrence - Time Of Day,Recurrence - Start Date,Recurrence - End Date,Recurrence - Frequency,Recurrence - Interval,Recurrence - Day,Recurrence - Day Of Month,Recurrence - Day Of Week,Recurrence - Day Of Week Index,Recurrence - Day of Week Day,Recurrence - Month Of Year,Recurrence - iCal,Recurrence - Workflow Manager,Created At,Updated At
,,,0,Emergency change,Use the Note field to provide a summary of the emergency change that was implemented.,,,emergency,,correction,,"Inform service owner of implemented emergency change
Update configuration management information
Update the capacity utilization overview
Update the continuity plan for the service infrastructure","'Update configuration management information' => 'Update the continuity plan for the service infrastructure'
'Update configuration management information' => 'Update the capacity utilization overview'","","","","","","","","","","","","","","",,2017-01-23T08:46:45-05:00,2017-11-17T10:30:31-06:00
,,,0,Weekly offsite storage of backup tapes,,These tasks need to be executed every Monday morning.,Unix Server,standard,infrastructure_change,maintenance,,"44
45",44 => 45,0,Central Time (US & Canada),09:00,2013-01-01,,weekly,1,1,"",0,,,"","DTSTART;TZID=CST:20130101T000000
RRULE:FREQ=WEEKLY;BYDAY=MO",ellen.brown@widget.com,2017-10-19T07:52:23-05:00,2017-10-19T07:52:23-05:00
```

[download CSV](https://developer.xurrent.com/csv/workflow_templates.csv)

## Adding Phases to a Workflow Template

A workflow template may be structured in phases. The phases of a workflow template can be specified in the `Phases` column. Separate the names of the phases with a line break.

## Adding Task Templates to a Workflow Template

Task templates can be related to a workflow template by specifying the subject of each task template in the `Task Templates` column. Separate the subjects of the task templates with a line break.

Because a workflow task template may be part of a phase, the subject of each workflow task template can be followed by the name of one of the workflow template’s phases. Do this by adding the ` / ` symbol to the subject of the workflow task template and follow it with the name of the phase.

## Linking Task Templates to Form a Workflow

When multiple task templates are related to a workflow template, these task templates can be linked together into a workflow. This is done using the `Workflow` column. In this column, the predecessor => successor links can be defined.

The following example shows how a workflow can be defined from four task templates. The subjects of these four task templates are A through D. In this example, the workflow starts with task template A. This first task template has two successors. These are task templates B and C. Task templates B and C are the predecessors of task template D, which is the final step of the workflow.

```
'A' => 'B'
'A' => 'C'
'B' => 'D'
'C' => 'D'
```

Each predecessor => successor link needs to be separated by a line break.
