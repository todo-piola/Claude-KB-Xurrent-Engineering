# Standard Service Requests API

## Fields

charge\_type
: *Optional* **[enum](../general/enumerations/index.html)** — Defines how the standard service request must be charged: as a Fixed Price or in Time and Materials.

created\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time at which the Standard service request was created.

id
: *Readonly* **[integer](../general/data_types.html)** — The unique ID of the Standard service request.

rate
: *Optional* **[decimal](../general/data_types.html)** — Defines the fixed price rate for the standard service request.

rate\_currency
: *Optional* **[reference](../general/data_types.html#currency)** — Defines the currency for the fixed price rate of the standard service request.

request\_template
: *Required* **[reference](../general/data_types.html#references) to [Request template](../request_templates.html)** — The request template related to the service offering. Only the request templates that are linked to the same service as the service offering can be selected.

resolution\_target
: *Optional* **[integer](../general/data_types.html)** — Number of minutes within which a request needs to have been completed when the request template has been applied to the request and the requester is covered by an SLA that is based on the service offering.

resolution\_target\_best\_effort
: *Optional* **[boolean](../general/data_types.html)** — Resolution target is Best Effort when the request template has been applied to the request and the requester is covered by an SLA that is based on the service offering.

resolution\_target\_in\_days
: *Optional* **[integer](../general/data_types.html)** — Number of business days within which a request needs to have been completed when the request template has been applied to the request and the requester is covered by an SLA that is based on the service offering.

response\_target
: *Optional* **[integer](../general/data_types.html)** — Number of minutes within which a response needs to have been provided for a request to which the request template has been applied and which requester is covered by an SLA that is based on the service offering.

response\_target\_best\_effort
: *Optional* **[boolean](../general/data_types.html)** — Response target is Best Effort when the request template has been applied to the request and the requester is covered by an SLA that is based on the service offering.

response\_target\_in\_days
: *Optional* **[integer](../general/data_types.html)** — Number of business days within which a response needs to have been provided for a request to which the request template has been applied and which requester is covered by an SLA that is based on the service offering.

support\_hours
: *Optional* **[reference](../general/data_types.html#references) to [Calendar](../calendars/index.html)** — A calendar that defines the support hours for a request to which the request template has been applied and which requester is covered by an SLA that is based on the service offering.

updated\_at
: *Readonly* **[datetime](../general/data_types.html)** — The date and time of the last update of the Standard service request. If the Standard service request has no updates it contains the `created_at` value.
