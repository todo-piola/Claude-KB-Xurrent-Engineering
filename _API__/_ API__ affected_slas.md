# Affected SLAs API

- [List affected SLAs](index.html#list-affected-slas)
- [Get a single affected SLA](index.html#get-a-single-affected-sla)
- [Fields](index.html#fields)

## List affected SLAs

List all affected SLAs for an account:

```
GET /affected_slas
```

### Response

```
status: 200 OK
```

```
[{"stopped_clock_at":null,"service_instance":{"name":"New York Network","id":73},"created_at":"2016-03-14T03:00:11-06:00","started_at":"2016-03-14T03:00:11-06:00","support_hours":{"name":"24x7 (Monday through Sunday)","id":29},"downtime_start_at":null,"actual_response_at":"2016-03-14T03:00:11-06:00","actual_resolution_duration":0,"updated_at":"2016-03-14T03:14:11-06:00","supplier":null,"stopped_clock_duration":0,"resolution_target_at":"2016-03-14T13:00:11-06:00","actual_response_duration":0,"support_team":{"name":"Operations","id":11},"response_target_at":"2016-03-14T04:00:11-06:00","id":214,"request":{"account":{"name":"Widget North America","id":"wna"},"id":70473,"subject":"Windows password reset required"},"downtime_duration":null,"downtime_end_at":null,"accountability":"supplier","time_zone":"Central Time (US & Canada)","sla":{"name":"End-User Network Connectivity for Widget North America, HQ (New York)","id":34},"impact":"medium","service_hours":null,"maximum_response_duration":60,"maximum_resolution_duration":600,"actual_resolution_at":"2016-03-14T03:00:11-06:00","first_line_team":null,"standard_service_request":null},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of affected SLAs.

### Collection Fields

By default [all fields](index.html#fields) will appear in collections of affected SLAs.

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `request` `sla` `service_instance` `next_target_at` `created_at` `updated_at`

### Sorting

By default a collection of affected SLAs is sorted **descending** by `id`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `request` `sla` `service_instance`

## Get a single affected SLA

```
GET /affected_slas/:id
```

### Response

```
status: 200 OK
```

```
{"stopped_clock_at":null,"service_instance":{"name":"Expense Reporting Production","id":63},"created_at":"2016-03-29T07:22:00-05:00","started_at":"2016-03-29T07:22:00-05:00","desired_completion_at":null,"next_target":"no_target","support_hours":{"name":"24x6 (Monday through Saturday)","id":33},"downtime_start_at":"2016-03-29T05:42:00-05:00","actual_response_at":"2016-03-29T07:22:00-05:00","actual_resolution_duration":1635,"updated_at":"2016-03-14T03:13:51-06:00","supplier":null,"stopped_clock_duration":0,"resolution_target_at":"2016-03-29T11:22:00-05:00","actual_response_duration":0,"support_team":{"name":"Application Development","id":7},"response_target_at":"2016-03-29T07:52:00-05:00","id":2,"request":{"id":70231,"subject":"Expense Reporting is down"},"downtime_duration":2747,"downtime_end_at":"2016-03-31T10:29:00-05:00","accountability":"provider","time_zone":"Central Time (US & Canada)","sla":{"name":"Standard Expense Reporting for Widget Data Center","id":104},"impact":"top","service_hours":{"name":"24x7 except Sunday 5:00am until Noon","id":30},"maximum_response_duration":30,"maximum_resolution_duration":240,"actual_resolution_at":"2016-03-31T10:37:00-05:00","first_line_team":null,"standard_service_request":null}
```

The response contains [these fields](index.html#fields).

## Fields

accountability
: *Optional* **[enum](../general/enumerations/index.html)** — The Accountability field is set to `provider` when the service instance of the affected SLA is the same as the service instance of the request to which the affected SLA is linked. It is set to `supplier` when the service instance of the request is situated lower in the service hierarchy than the service instance of the affected SLA. It is set to `sla_not_affected` when the provider of the service instance that is linked to the affected SLA no longer has a responsibility for completing the request. Valid values are:
: - `provider`: Provider
 - `supplier`: Supplier
 - `sla_not_affected`: SLA Not Affected

actual\_resolution\_at
: *Readonly* **[datetime](../general/data_types.html)** — The current date and time is filled out in the Actual resolution field when the status of the request has been set to “Completed”.

actual\_resolution\_duration
: *Readonly* **[integer](../general/data_types.html)** — The Actual resolution duration field value is automatically calculated using the date and time in the Started field, the date and time in the Actual resolution field, and the calendar selected in the Support hours field of the affected SLA.

actual\_response\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Actual response field is empty when the service instance (SI) that is selected in the request is the same as the related SI, and the request has not yet been saved with one of the following status values since this SI was linked to it:

actual\_response\_duration
: *Readonly* **[integer](../general/data_types.html)** — The Actual response duration field value is automatically calculated using the date and time in the Started field, the date and time in the Actual response field, and the calendar selected in the Support hours field of the affected SLA.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the affected SLA was created.

desired\_completion\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Desired completion field is the desired completion of the request that the affected SLA is linked to.

downtime\_duration
: *Readonly* **[integer](../general/data_types.html)** — The Downtime duration field value is automatically calculated using the date and time in the Downtime start field, the date and time in the Downtime end field, and the calendar selected in the Service hours field of the affected SLA.

downtime\_end\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Downtime end field is automatically set to the value in the Downtime end field of the request to which the affected SLA is linked.

downtime\_start\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Downtime start field is automatically set to the value in the Downtime start field of the request to which the affected SLA is linked.

first\_line\_team
: *Readonly* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The First line team field is automatically set to the team that, at the time the affected SLA was created, was selected in the First line team field of the related service instance.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the affected SLA.

impact
: *Readonly* **[enum](../general/enumerations/index.html)** — The Impact field is automatically set to the impact selected in the request, provided that the service instance (SI) that is selected in the request is the same as the related SI. Valid values are:
: - `low`: Low - Service Degraded for One User
 - `medium`: Medium - Service Down for One User
 - `high`: High - Service Degraded for Several Users
 - `top`: Top - Service Down for Several Users

maximum\_resolution\_duration
: *Readonly* **[integer](../general/data_types.html)** — The Maximum resolution duration field is automatically set to the number of minutes that were specified, at the time the impact level was assigned to the affected SLA, in the Resolution target field for this impact level in the service offering of the related service level agreement.

maximum\_resolution\_duration\_in\_days
: *Readonly* **[integer](../general/data_types.html)** — The Maximum resolution duration in days field is automatically set to the number of business days that were specified, at the time the impact level was assigned to the affected SLA, in the Resolution target field for this impact level in the service offering of the related service level agreement.

maximum\_response\_duration
: *Readonly* **[integer](../general/data_types.html)** — The Maximum response duration field is automatically set to the number of minutes that were specified, at the time the impact level was assigned to the affected SLA, in the Response target field for this impact level in the service offering of the related service level agreement.

maximum\_response\_duration\_in\_days
: *Readonly* **[integer](../general/data_types.html)** — The Maximum response duration in days field is automatically set to the number of business days that were specified, at the time the impact level was assigned to the affected SLA, in the Response target field for this impact level in the service offering of the related service level agreement.

next\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Next target field value is empty when the Accountability field is set to `sla_not_affected` or when the Actual resolution field contains a value. It is set to `clock_stopped` when the clock has been stopped for the affected SLA. The next target equals the response target when a response target exists and the Actual response field is still empty. Otherwise, the next target equals the desired completion when a desired completion exists and a resolution target exists and the desired completion is greater than the resolution target. Otherwise the next target is the resolution target when a resolution target exists. In all other cases, the next target is `best_effort`.

provider\_not\_accountable
: *Readonly* **[boolean](../general/data_types.html)** — The Provider not accountable field value is automatically set to `true` when the provider currently indicates not to be accountable.

provider\_was\_not\_accountable
: *Readonly* **[boolean](../general/data_types.html)** — The Provider was not accountable field value is automatically set to `true` when the provider has at any point in time indicated not to be accountable.

request
: *Readonly* **[reference](../general/data_types.html#references) to [Request](../requests.html)** — The Request field is automatically set to the request for which the affected SLA was generated.

resolution\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Resolution target field value is automatically calculated using the date and time in the Started field, the value in Maximum resolution duration field, and the calendar selected in the Support hours field of the affected SLA.

response\_target\_at
: *Readonly* **[datetime](../general/data_types.html)** — The Response target field value is automatically calculated using the date and time in the Started field, the value in the Maximum response duration field, and the calendar selected in the Support hours field of the affected SLA.

service\_hours
: *Readonly* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — If the impact of the affected SLA is “Top - Service Down for Several Users”, the Service hours field is automatically set to the service hours calendar of the service offering of the related service level agreement.

service\_instance
: *Readonly* **[reference](../general/data_types.html#references) to [Service Instance](../service_instances/index.html)** — The Service instance field is automatically set to the [Service Instance](../service_instances/index.html) that, at the time the affected SLA was created, was selected in the Service instance field of the related service level agreement.

sla
: *Readonly* **[reference](../general/data_types.html#references) to [Service Level Agreement](../service_level_agreements.html)** — The Service level agreement field is automatically set to the service level agreement that is considered affected.

standard\_service\_request
: *Readonly* **[reference](../general/data_types.html#references) to [Standard Service Request](../service_offerings/standard_service_requests/index.html)** — The Standard service request field is automatically set to the standard service request that is linked to the service offering of the service level agreement and which response and resolution targets were used to calculate the `response_target_at` and `resolution_target_at` for the affected SLA.

started\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the clock was started for the calculation of the affected SLA’s response and resolution targets and durations.

stopped\_clock\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the clock was stopped for the calculation of the affected SLA’s response and resolution durations.

stopped\_clock\_duration
: *Readonly* **[integer](../general/data_types.html)**, default: `0` — The Stopped clock duration field value is automatically calculated using the date and time at which the clock was stopped, the date and time at which the clock was started again, the calendar selected in the Support hours field of the affected SLA, and the previous value to which this field was set.

supplier
: *Readonly* **[reference](../general/data_types.html#references) to [Organization](../organizations.html)** — The Supplier field is automatically set to the [Organization](../organizations.html) that, at the time the affected SLA was created, was selected in the Service provider field of the related service instance. This field is only filled out, however, if this service provider is an external organization.

support\_hours
: *Readonly* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Support hours field is automatically set to the support hours [Calendar](../calendars/index.html) that was selected for the impact level specified above in the service offering of the related service level agreement.

support\_team
: *Readonly* **[reference](../general/data_types.html#references) to [Team](../teams.html)** — The Support team field is automatically set to the team that, at the time the affected SLA was created, was selected in the Support team field of the related service instance.

time\_zone
: *Readonly* **[time\_zone](../general/data_types.html)** — The Time zone field is automatically set to the value that was specified, at the time the affected SLA was created, in the service offering of the related service level agreement.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the affected SLA. If the affected SLA has no updates it contains the `created_at` value.
