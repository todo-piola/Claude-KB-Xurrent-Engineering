# Computer Telephony Integration (CTI)

Organizations can configure an additional option in their IP telephony system
for launching the [Service Desk
console](https://help.xurrent.com/help/service_desk_console). Once this option has
been added, the organization’s service desk analysts will be able to use it
whenever a call is routed to the [softphone](http://en.wikipedia.org/wiki/Softphone) on
their computers. When used, the incoming call is picked up while at the same
time a new browser window presents the details and previously registered
requests of the caller. If a new request needs to be opened for the caller, the
analyst only needs to press the `Enter` key.

To configure this option, the IP telephony system needs to be told to launch a
new browser window with a URL that ends with the telephone number of the caller.
This URL must adhere to the following syntax:

```
https://example.xurrent.com/sd?telephone=1234567890
```

In the URL above, `example` represents the ID of the Xurrent account. Replace it
with the ID of the Xurrent account of the organization for which the computer
telephony integration is to be configured.

Note that the REST API can be used in a similar fashion to [retrieve a Person
record using a telephone
number](../people.html#using-a-phone-number-to-get-a-person).

## Testing

After substituting `example` with the ID of an organization’s Xurrent account, the
URL can be tested using a browser. Enter the URL in the address bar of the
browser and press `Enter`.

Be sure to log into Xurrent as a user of the account who has the Service Desk
Analyst role. Use a telephone number of a Person who this user is able to select
manually in the Service Desk console.

## Number Matching

It does not matter how the phone numbers are registered in Xurrent. A number could
be written as `+1 (123) 456 7890` or `123-456-7890` or just `4567890`.
Similarly, the phone system can add the phone number at the end of the URL as
`+11234567890` or `0011234567890` or `4567890`. Only the numbers will be used to
find a match. Any other characters are ignored. When spaces are included in the
URLs that the phone system generates, then each space gets encoded properly as
`%20`.

People can call from their work, mobile or home number. As long as the number is
registered in Xurrent for a Person, Xurrent finds this Person. When the number is used
by multiple people, these people are suggested as options for the Requester field
when the Service Desk console is launched.

## Support ID

Many organizations use an automatic call distribution (ACD) system to collect
some information from callers before assigning their call to an available
service desk analyst. A caller could, for example, be asked to enter his/her
security badge number or customer number. When the Support ID field of the Person
records is populated with this number, the ACD can pass the value that the caller
said or entered to Xurrent.

To ask Xurrent’s CTI functionality to use the Support ID to look up a caller, the URL
must use the following syntax:

```
https://example.xurrent.com/sd?supportID=33821
```

When the same customer number is entered in the Support ID field of each contact
person of the corresponding customer organization, these people get listed as
options for the Requester field when the Service Desk console is launched.

## Employee ID

Rather than using the telephone number or support ID of the caller, it is also
possible to look up the caller using his/her employee ID. Organizations can use
their ACD to ask for the caller’s employee number. The ACD can then pass the
value that the caller said or entered to Xurrent’s CTI functionality to ensure that
the caller gets selected automatically in the Requester field of the Service Desk
console.

To use the employee ID to look up a caller, the URL must use the following syntax:

```
https://example.xurrent.com/sd?employeeID=40001652
```

## Request ID

Instead of using the telephone number or Support ID of the caller it is also
possible to use the ID of a Request that was requested by the caller. In this
case, the URL must use the following syntax:

```
https://example.xurrent.com/sd?request=70464
```

The browser window will show the details and previously registered requests of
the caller. The provided Request ID will automatically be selected from the list
of previously registered requests and the details of that Request will be
loaded.

When the Request ID cannot be found within the last 50 registered requests of
the caller, the details of the Request will not be loaded automatically.

## Proving Fallback Parameters

Xurrent’s CTI functionality also offers the ability to provide multiple parameters.
This can be useful, for example, when the ACD is programmed to ask a caller for
the number of the request that he/she is calling about. But if the caller does not
enter a number because the call is about a new issue, or if the caller provided a
request number that does not exist, it may be helpful if the telephony integration
falls back on the caller’s telephone number. That way, the Service Desk console
would still open automatically for the agent who accepts the call and even though
a previously registered request will not be presented, the Service Desk console
will still automatically select the caller in the Requester field and list all of
this person’s previously registered requests.

The following parameters can be provided:

- `request`
- `employeeID`
- `supportID`
- `telephone`

If all of them are provided, they are processed in the order listed above. This means
that the CTI functionality will first attempt to find a match on the request ID. If
such a match could not be found, it will try to find a person record using the
employee number that was provided, etc.

An example of a valid CTI URL that provides two parameters to Xurrent is presented below:

```
https://example.xurrent.com/sd?request=1081652&telephone=2123682651
```

## Bi-directional

The computer telephony integration is bi-directional. Xurrent automatically
hyperlinks the telephone numbers it displays. When a user clicks on a telephone
number, the softphone (if properly configured) will be launched to call the
number.
