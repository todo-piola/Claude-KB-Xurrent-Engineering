# Project Templates Import

Project Templates can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Project Templates import file can be found in [Project Templates API - Fields](../../project_templates/index.html#fields).

## CSV Example

```
ID,Source,Source ID,Disabled,Subject,Phases,Task Templates,Workflow,Created At,Updated At
,,,0,New project - Initiation phase only,"Initiation
Approval","Estimate internal effort / Initiation
Estimate project value / Initiation
Find sponsor for project / Initiation
Obtain approval for project / Approval","'Estimate internal effort' => 'Find sponsor for project'
'Estimate project value' => 'Find sponsor for project'
'Find sponsor for project' => 'Obtain approval for project'",2017-01-23T08:46:45-05:00,2017-11-17T10:30:31-06:00
```

[download CSV](https://developer.xurrent.com/csv/project_templates.csv)

## Adding Phases to a Project Template

A project template must have at least one phase. The phases of a project template can be specified in the `Phases` column. Separate the names of the phases with a line break.

## Adding Project Task Templates to a Project Template

Project task templates can be related to a project template by specifying the subject of each project task template in the `Task Templates` column. Separate the subjects of the project task templates with a line break.

Because a project task template needs to be part of a phase, the subject of each project task template must be followed by the name of one of the project template’s phases. Do this by adding the `/` symbol to the subject of the project task template and follow it with the name of the phase.

## Linking Project Task Templates to Form a Workflow

When multiple project task templates are related to a project template, these task templates can be linked together into a workflow. This is done using the `Workflow` column. In this column, the predecessor => successor links can be defined.

The example below shows how a workflow can be defined from four project task templates. In this example, the workflow starts with two project task templates in parallel. These two templates are ‘Estimate internal effort’ and ‘Estimate project value’. These two templates have one successor. This successor is ‘Find sponsor for project’, which is followed by ‘Obtain approval for project’, which the final step of the workflow .

```
Estimate internal effort => Find sponsor for project
Estimate project value => Find sponsor for project
Find sponsor for project => Obtain approval for project
```

Each predecessor => successor link needs to be separated by a line break.
