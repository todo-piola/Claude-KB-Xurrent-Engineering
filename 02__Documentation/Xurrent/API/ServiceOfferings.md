# Service Offerings API

- [List service offerings](index.html#list-service-offerings)
- [Get a single service offering](index.html#get-a-single-service-offering)
- [Create a service offering](index.html#create-a-service-offering)
- [Update a service offering](index.html#update-a-service-offering)
- [Fields](index.html#fields)

## List service offerings

List all service offerings for an account:

```
GET /service_offerings
```

### Response

```
status: 200 OK
```

```
[{"name":"Bronze Conference Room","created_at":"2016-03-14T03:10:41-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:41-06:00","service":{"name":"Conference Room","id":10,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"id":20,"status":"available"},{"name":"Bronze Local Printing","created_at":"2016-03-14T03:10:41-06:00","sourceID":null,"updated_at":"2016-03-14T03:10:41-06:00","service":{"name":"Local Printing","id":17,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"id":21,"status":"available"},"..."]
```

The response contains [these fields](index.html#collection-fields) by default. [Filtering](index.html#filtering) and [pagination](../general/pagination.html) are available to reduce/limit the collection of service offerings.

### Predefined Filters

The following [predefined filters](../general/filtering.html#predefined-filters) are available:

- `/service_offerings/catalog`: List all catalog service offerings
- `/service_offerings/portfolio`: List all portfolio service offerings

### Collection Fields

By default the following [fields](index.html#fields) will appear in collections of service offerings:

`id` `sourceID` `name` `status` `service` `created_at` `updated_at`

Obtain a different set of [fields](index.html#fields) using the [?fields= parameter](../general/field_selection/index.html#collection-of-resources).

### Filtering

[Filtering](../general/filtering.html) is available for the following [fields](index.html#fields):

`id` `source` `sourceID` `name` `status` `service` `created_at` `updated_at`

### Sorting

By default a collection of service offerings is sorted **ascending** by `name`.

The following [fields](index.html#fields) are accepted by the [?sort= parameter](../general/ordering.html):

`id` `sourceID` `name` `status` `service` `created_at` `updated_at`

## Get a single service offering

```
GET /service_offerings/:id
```

### Response

```
status: 200 OK
```

```
{"response_target_high":25,"prerequisites":"In order for the customer organization to benefit from the projection capabilities in the conference rooms, the following requirement needs to be met by the customer organization:\n- A workstation compliant with the Widget Hardware Standards & Guidelines for each user of the projector.\nThe Widget Data Center service provider organization cannot be held accountable for breaches of the service level targets caused by the failure of the customer organization to meet this requirement.","name":"Bronze Conference Room","support_hours_medium":{"name":"Monday through Friday, 7:00am until 5:00pm","id":34},"created_at":"2016-03-14T03:10:41-06:00","support_hours_low":{"name":"Monday through Friday, 7:00am until 5:00pm","id":34},"sourceID":null,"updated_at":"2016-03-14T03:10:41-06:00","support_hours_top":{"name":"Monday through Friday, 7:00am until 5:00pm","id":34},"service":{"name":"Conference Room","id":10,"provider":{"name":"Widget Data Center, Internal IT","id":32}},"review_frequency":"yearly","resolution_target_low":240,"maximum_risk_of_data_loss":"Data Is Not Backed Up","support_hours_high":{"name":"Monday through Friday, 7:00am until 5:00pm","id":34},"resolution_target_top":60,"restore_duration":"Data Is Not Backed Up","limitations":"The service provider can be held accountable for the service level targets up to the following capacity limit:\n- 1 projector per meeting room,\n- 1 Polycom teleconferencing station.","id":20,"availability":99.0,"termination":"Any service level agreement based on this service offering remains into effect until either the customer or the service provider organization terminates it, taking into account a twelve-month termination period.\nCustomer organizations may also terminate their service level agreements based on this service offering on the date that a charge change announced by the service provider organization becomes effective, taking into account a one-month termination period.","responses_within_target":80,"resolutions_within_target":80,"offline_backup_schedule":"Data Is Not Backed Up","response_target_medium":25,"resolution_target_medium":120,"performance":"The time it takes for a projector to be warmed-up is not to take longer than 2 minutes.","penalties":"During each SLA review meeting, special attention will be paid to service level targets (SLTs) that were breached during the past SLA evaluation term. For each SLT that was breached, the service level manager will present the actions that Widget Data Center's Internal IT department has taken, or will take, to ensure that the SLT will not be breached again.","charges":"$7,400.00 per conference room per annum.\n\nCustomers are notified of any charge adjustments at least 6 months before the new charges become effective.","time_zone":"Central Time (US & Canada)","summary":"The bronze level of service for the Conference Room service offers an availability target of 99.0% during service hours from Monday through Friday from 7:00am until 5:00pm (CST), which is roughly equal to a maximum outage duration of 2 hours and 10 minutes per month. The resolution target of a service outage (i.e. an incident that prevents multiple users from using the service) is 1 support hour. Service degradations that affect multiple users have a resolution target of 2 support hours. At least 80% of the incidents covered by an SLA of this offering are to be resolved within the resolution target. In case of a disaster, the service will not be made available again from a continuity site. Customers with an active SLA based on this offering are charged $7,400.00 per conference room, per annum.","response_target_low":30,"report_frequency":"monthly","reliability":4,"status":"available","source":null,"service_hours":{"name":"Monday through Friday, 7:00am until 5:00pm","id":34},"response_target_top":20,"resolution_target_high":120,"continuity":"Service will not be recovered at a continuity site."}
```

The response contains [these fields](index.html#fields).

## Create a service offering

```
POST /service_offerings
```

When creating a new service offering [these fields](index.html#fields) are available.

### Response

```
status: 201 Created
```

```
{"availability":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the created service offering and is similar to the response in [Get a single service offering](index.html#get-a-single-service-offering)

## Update a service offering

```
PATCH /service_offerings/:id
```

When updating a service offering [these fields](index.html#fields) are available.

### Response

```
status: 200 OK
```

```
{"availability":"...","...":"..."}
```

The response contains [all fields](index.html#fields) of the updated service offering and is similar to the response in [Get a single service offering](index.html#get-a-single-service-offering)

## Fields

attachments
: *Readonly* **aggregated Attachments**

availability
: *Optional* **[decimal](../general/data_types.html)** — The Availability field is used to specify the duration, expressed as percentage of the total number of service hours, during which the service is to be available to customers with an active SLA that is based on the service offering.

charge\_type\_high
: *Optional* **[enum](../general/enumerations/index.html)** — Defines how a high incident must be charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

charge\_type\_low
: *Optional* **[enum](../general/enumerations/index.html)** — Defines how a low incident must be charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

charge\_type\_medium
: *Optional* **[enum](../general/enumerations/index.html)** — Defines how a medium incident must be charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

charge\_type\_rfc
: *Optional* **[enum](../general/enumerations/index.html)** — Defines how a RFC must be charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

charge\_type\_rfi
: *Optional* **[enum](../general/enumerations/index.html)** — Defines how a RFI must be charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

charge\_type\_top
: *Optional* **[enum](../general/enumerations/index.html)** — Defines how a top incident must be charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

charge\_type\_case
: *Optional* **[enum](../general/enumerations/index.html)** — Defines how a case must be charged. Valid values are:
: - `fixed_price`: Fixed Price
 - `time_material`: Time and Material

charges
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Charges field is used to describe the amount that the service provider will charge the customer for the delivery of the service per charge driver, per charge term.

charges\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Charges field.

continuity
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Continuity measures field is used to specify the continuity measures for the service offering.

continuity\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Continuity field.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the service offering was created.

default\_effort\_class
: *Optional* **[reference](../effort_classes.html)** — The effort class that is selected by default, when someone registers time on a request with an active affected SLA based on the service offering.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the service offering.

limitations
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Limitations field is used to specify the limitations that apply to the service level agreements that are based on the service offering.

limitations\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Limitations field.

maximum\_risk\_of\_data\_loss
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Maximum risk of data loss field is used to enter the maximum number of hours of data loss that customers could experience if the most recent backup needs to be restored.
: Deprecated - The `maximum_risk_of_data_loss` field is being phased out. Use the `recovery_point_objective` field instead.

name
: *Required* **[string](../general/data_types.html) (max 80)** — The Name field is used to enter the name of the service offering using the following syntax:

offline\_backup\_schedule
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Offline backup schedule field is used to specify on which days and during which periods the offline backup is performed.
: Deprecated - The `offline_backup_schedule` field is being phased out. Use the `continuity` field instead.

penalties
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Penalties field is used to specify what the penalties will be for the service provider organization if a service level target has been breached.

penalties\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Penalties field.

performance
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Performance field is used to describe the transaction(s) and the maximum time these transaction(s) can take to complete.

performance\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Performance field.

prerequisites
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Prerequisites field is used to specify which requirements need to be met by the customer in order for the customer to be able to benefit from the service. The service provider cannot be held accountable for breaches of the service level targets caused by a failure of the customer to meet one or more of these prerequisites.

prerequisites\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Prerequisites field.

rate\_high
: *Optional* **[decimal](../general/data_types.html)** — Defines the fixed price rate for a high incident.

rate\_high\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — Defines the currency for the fixed price rate of a high incident.

rate\_low
: *Optional* **[decimal](../general/data_types.html)** — Defines the fixed price rate for a low incident.

rate\_low\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — Defines the currency for the fixed price rate of a low incident.

rate\_medium
: *Optional* **[decimal](../general/data_types.html)** — Defines the fixed price rate for a medium incident.

rate\_medium\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — Defines the currency for the fixed price rate of a medium incident.

rate\_rfc
: *Optional* **[decimal](../general/data_types.html)** — Defines the fixed price rate for a RFC.

rate\_rfc\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — Defines the currency for the fixed price rate of a RFC.

rate\_rfi
: *Optional* **[decimal](../general/data_types.html)** — Defines the fixed price rate for a RFI.

rate\_rfi\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — Defines the currency for the fixed price rate of a RFI.

rate\_top
: *Optional* **[decimal](../general/data_types.html)** — Defines the fixed price rate for a top incident.

rate\_top\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — Defines the currency for the fixed price rate of a top incident.

rate\_case
: *Optional* **[decimal](../general/data_types.html)** — Defines the fixed price rate for a Case.

rate\_case\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — Defines the currency for the fixed price rate of a Case.

recovery\_time\_objective
: *Optional* **[integer](../general/data_types.html)** — The Recovery Time Objective (RTO) field is used to specify the targeted duration of time and a service level within which a business process must be restored after a disaster (or disruption) in order to avoid unacceptable consequences associated with a break in business continuity.

recovery\_point\_objective
: *Optional* **[integer](../general/data_types.html)** — The Recovery Point Objective (RPO) field is used to specify the maximum targeted period in which data (transactions) might be lost from an IT service due to a major incident.

reliability
: *Optional* **[integer](../general/data_types.html)** — The Reliability field is used to specify the maximum number of times per month that the service may become unavailable to customers with an active SLA that is based on the service offering.

report\_frequency
: *Optional* **[enum](../general/enumerations/index.html)**, default: `no_commitment` — The Report frequency field is used to specify how often the representative of a customer of an active SLA that is based on the service offering will receive a report comparing the service level targets specified in the service offering with the actual level of service provided. Valid values are:
: - `daily`: Daily
 - `weekly`: Weekly
 - `once_every_2_weeks`: Once Every 2 Weeks
 - `monthly`: Monthly
 - `once_every_2_months`: Once Every 2 Months
 - `quarterly`: Quarterly
 - `once_every_6_months`: Once Every 6 Months
 - `yearly`: Yearly
 - `once_every_2_years`: Once Every 2 Years
 - `no_commitment`: No Commitment

resolution\_target\_high
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of hours and minutes within which a request with the impact value “High – Service Degraded for Several Users” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_high\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of business days within which a request with the impact value “High – Service Degraded for Several Users” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_low
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of hours and minutes within which a request with the impact value “Low – Service Degraded for One User” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_low\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of business days within which a request with the impact value “Low – Service Degraded for One User” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_medium
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of hours and minutes within which a request with the impact value “Medium – Service Down for One User” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_medium\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of business days within which a request with the impact value “Medium – Service Down for One User” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_rfc
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of hours and minutes within which a request with the category “RFC – Request for Change” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_rfc\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of business days within which a request with the category “RFC – Request for Change” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_rfi
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of hours and minutes within which a request with the category “RFI – Request for Information” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_rfi\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of business days within which a request with the category “RFI – Request for Information” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_top
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of hours and minutes within which a request with the impact value “Top – Service Down for Several Users” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_top\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of business days within which a request with the impact value “Top – Service Down for Several Users” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_case
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of hours and minutes within which a request with the category “Case” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_case\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Resolution target field is used to enter the number of business days within which a request with the category “Case” is to be resolved when it affects an active SLA that is based on the service offering.

resolution\_target\_notification\_scheme\_high
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The resolution target notification scheme for a request with the impact “High — Service Degraded for Several Users” when it affects an active SLA that is based on the service offering.

resolution\_target\_notification\_scheme\_low
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The resolution target notification scheme for a request with the impact “Low — Service Degraded for One User” when it affects an active SLA that is based on the service offering.

resolution\_target\_notification\_scheme\_medium
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The resolution target notification scheme for a request with the impact “Medium — Service Down for One User” when it affects an active SLA that is based on the service offering.

resolution\_target\_notification\_scheme\_top
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The resolution target notification scheme for a request with the impact “Top — Service Down for Several Users” when it affects an active SLA that is based on the service offering.

resolutions\_within\_target
: *Optional* **[integer](../general/data_types.html)** — The Resolutions within target field is used to enter the minimum percentage of incidents that is to be resolved before their resolution target.

response\_target\_high
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of hours and minutes within which a response needs to have been provided for a request with the impact “High – Service Degraded for Several Users” when it affects an active SLA that is based on the service offering.

response\_target\_high\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of business days within which a response needs to have been provided for a request with the impact “High – Service Degraded for Several Users” when it affects an active SLA that is based on the service offering.

response\_target\_low
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of hours and minutes within which a response needs to have been provided for a request with the impact “Low – Service Degraded for One User” when it affects an active SLA that is based on the service offering.

response\_target\_low\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of business days within which a response needs to have been provided for a request with the impact “Low – Service Degraded for One User” when it affects an active SLA that is based on the service offering.

response\_target\_medium
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of hours and minutes within which a response needs to have been provided for a request with the impact “Medium – Service Down for One User” when it affects an active SLA that is based on the service offering.

response\_target\_medium\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of business days within which a response needs to have been provided for a request with the impact “Medium – Service Down for One User” when it affects an active SLA that is based on the service offering.

response\_target\_rfc
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of hours and minutes within which a response needs to have been provided for a request with the category “RFC – Request for Change” when it affects an active SLA that is based on the service offering.

response\_target\_rfc\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of business days within which a response needs to have been provided for a request with the category “RFC – Request for Change” when it affects an active SLA that is based on the service offering.

response\_target\_rfi
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of hours and minutes within which a response needs to have been provided for a request with the category “RFI – Request for Information” when it affects an active SLA that is based on the service offering.

response\_target\_rfi\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of business days within which a response needs to have been provided for a request with the category “RFI – Request for Information” when it affects an active SLA that is based on the service offering.

response\_target\_top
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of hours and minutes within which a response needs to have been provided for a request with the impact “Top – Service Down for Several Users” when it affects an active SLA that is based on the service offering.

response\_target\_top\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of business days within which a response needs to have been provided for a request with the impact “Top – Service Down for Several Users” when it affects an active SLA that is based on the service offering.

response\_target\_case
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of hours and minutes within which a response needs to have been provided for a request with the category “Case” when it affects an active SLA that is based on the service offering.

response\_target\_case\_in\_days
: *Optional* **[integer](../general/data_types.html)** — This Response target field is used to enter the number of business days within which a response needs to have been provided for a request with the category “Case” when it affects an active SLA that is based on the service offering.

response\_target\_notification\_scheme\_high
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The response target notification scheme for a request with the impact “High — Service Degraded for Several Users” when it affects an active SLA that is based on the service offering.

response\_target\_notification\_scheme\_low
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The response target notification scheme for a request with the impact “Low — Service Degraded for One User” when it affects an active SLA that is based on the service offering.

response\_target\_notification\_scheme\_medium
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The response target notification scheme for a request with the impact “Medium — Service Down for One User” when it affects an active SLA that is based on the service offering.

response\_target\_notification\_scheme\_top
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The response target notification scheme for a request with the impact “Top — Service Down for Several Users” when it affects an active SLA that is based on the service offering.

responses\_within\_target
: *Optional* **[integer](../general/data_types.html)** — The Responses within target field is used to enter the minimum percentage of incidents that is to be responded to before their response target.

restore\_duration
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Restore duration field is used to enter the number of hours within which a restore is to be completed after having received the request or approval for a restore from the customer.
: Deprecated - The `restore_duration` field is being phased out. Use the `recovery_time_objective` field instead.

review\_frequency
: *Optional* **[enum](../general/enumerations/index.html)**, default: `no_commitment` — The Review frequency field is used to specify how often an active SLA that is based on the service offering will be reviewed with the representative of its customer. Valid values are:
: - `daily`: Daily
 - `weekly`: Weekly
 - `once_every_2_weeks`: Once Every 2 Weeks
 - `monthly`: Monthly
 - `once_every_2_months`: Once Every 2 Months
 - `quarterly`: Quarterly
 - `once_every_6_months`: Once Every 6 Months
 - `yearly`: Yearly
 - `once_every_2_years`: Once Every 2 Years
 - `no_commitment`: No Commitment

service
: *Required* **[reference](../general/data_types.html#references) to [Service](../services.html)** — The Service field is used to select the [Service](../services.html) for which the service offering is being prepared.

service\_hours
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — The Service hours field is used to select a [Calendar](../calendars/index.html) that defines the hours during which the service is supposed to be available.

sla\_notification\_scheme\_high
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The SLA notification scheme for a request with the impact “High — Service Degraded for Several Users” when it affects an active SLA that is based on the service offering. **Deprecated**: use `resolution_target_notification_scheme_high` instead.

sla\_notification\_scheme\_low
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The SLA notification scheme for a request with the impact “Low — Service Degraded for One User” when it affects an active SLA that is based on the service offering. **Deprecated**: use `resolution_target_notification_scheme_low` instead.

sla\_notification\_scheme\_medium
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The SLA notification scheme for a request with the impact “Medium — Service Down for One User” when it affects an active SLA that is based on the service offering. **Deprecated**: use `resolution_target_notification_scheme_medium` instead.

sla\_notification\_scheme\_top
: *Optional* **[reference](../general/data_types.html#references) to [SLA Notification Scheme](../sla_notification_schemes/index.html)** — The SLA notification scheme for a request with the impact “Top — Service Down for Several Users” when it affects an active SLA that is based on the service offering. **Deprecated**: use `resolution_target_notification_scheme_top` instead.

source
: *Optional* **[string](../general/data_types.html) (max 30)** - See [source](../general/source.html)

sourceID
: *Optional* **[string](../general/data_types.html) (max 128)** - See [source](../general/source.html)

status
: *Optional* **[enum](../general/enumerations/index.html)**, default: `planned` — The Status field is used to select the current status of the service offering. Valid values are:
: - `planned`: Planned
 - `unpublished`: Unpublished
 - `available`: Available
 - `temporarily_unavailable`: Temporarily Unavailable
 - `discontinued`: Discontinued

summary
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Summary field is used to enter a high-level description of the differentiators between this service offering and other service offerings that have already been, or could be, prepared for the same service.

summary\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The inline attachments used in the Summary field.

support\_hours\_high
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — This Support hours field is used to select a calendar that defines the support hours for a request with the impact “High – Service Degraded for Several Users” when it affects an active SLA that is based on the service offering.

support\_hours\_low
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — This Support hours field is used to select a calendar that defines the support hours for a request with the impact “Low – Service Degraded for One User” when it affects an active SLA that is based on the service offering.

support\_hours\_medium
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — This Support hours field is used to select a calendar that defines the support hours for a request with the impact “Medium – Service Down for One User” when it affects an active SLA that is based on the service offering.

support\_hours\_rfc
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — This Support hours field is used to select a calendar that defines the support hours for a request with the category “RFC – Request for Change” when it affects an active SLA that is based on the service offering.

support\_hours\_rfi
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — This Support hours field is used to select a calendar that defines the support hours for a request with the category “RFI – Request for Information” when it affects an active SLA that is based on the service offering.

support\_hours\_top
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — This Support hours field is used to select a calendar that defines the support hours for a request with the impact “Top – Service Down for Several Users” when it affects an active SLA that is based on the service offering.

support\_hours\_case
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — This Support hours field is used to select a calendar that defines the support hours for a request with the category “Case” when it affects an active SLA that is based on the service offering.

termination
: *Optional* **[text](../general/data_types.html) (max 64KB)** — The Termination field is used to describe the length of notice required for changing or terminating the service level agreement.

termination\_attachments
: *Writeonly* **[attachments](../general/data_types.html#attachments)** The attachments used in the Termination field.

time\_zone
: *Optional* **[time\_zone](../general/data_types.html)** — The Time zone field is used to select the time zone that applies to the selected service hours.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the service offering. If the service offering has no updates it contains the `created_at` value.

waiting\_for\_customer\_follow\_up
: *Optional* **[reference](../general/data_types.html#references) to [Waiting for Customer Follow-Up](../waiting_for_customer_follow_ups/index.html)** — The waiting for customer follow-up containing the rules when the request has the status waiting for customer.
