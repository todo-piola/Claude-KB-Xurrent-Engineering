---
title: "Introducing Reservations"
date: "July 21, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/introducing-reservations"
slug: "introducing-reservations"
---

# Introducing Reservations

A major new capability has become available in Xurrent to make it possible for organizations to allow their people to reserve certain configuration items for a period of time.  To explain how to make use of the new reservations functionality, let’s assume that an organization has a few pool cars that its employees can use whenever they need one.

The very first step is for a configuration manager to make sure all the pool cars that people should be able to reserve are registered as a configuration item.  Once this is done, it is time to register a reservation offering for these configuration items.  A new reservation offering can be created by going to the Records console, selecting the option ‘Reservation Offerings’ and pressing the toolbar button with the big plus sign.

In a reservation offering, the configuration manager can specify the hours during which items can be reserved, what the minimum and maximum duration of a reservation is and the time increments for the duration of a reservation.  It is also possible to specify that some time is needed between each reservation of an item.  This time may be needed to take back the item and prepare it for the next person who reserved it.  A minimum advance duration can be specified to make sure that there is enough time available to get a reserved item ready from the moment it is reserved.  The Max. advance duration field can be used to prevent items from being reserved too far in advance (e.g. beyond their useful life).

And of course it is possible to relate one or more configuration items to a reservation offering to let Xurrent know which items people are allowed to reserve.

Linking filters to a reservation offering allows people who are making a reservation to filter the list of items down so that they can see the availability of only the kind of item that they want to reserve.  For example, if there were many pool cars to choose from, it may be useful to allow people to only look for pickup trucks rather than sedans.  Or it might be helpful if people could filter by maximum occupancy if they need a car that can transport at least 4 people (in which case a UI extension with a filterable custom field in which the maximum occupancy is specified would be needed for the configuration items).

A service instance needs to be selected in a reservation offering to make sure that only people who are covered by an active SLA for that service instance will be able to make use of this reservation offering.

The Initial status field is set to ‘Confirmed’ by default.  If left unchanged, any reservation made using the reservation offering will be confirmed right away.  Using ‘Confirmed’ as the initial status means that the requester does not need to wait for a confirmation.  But there are some types of reservations that may, for example, first require an approval.  For such reservations, the Initial status field should be set to ‘Pending’.  Once approved, a reservation which status is ‘Pending’ can be updated to ‘Confirmed’, either manually or by an [automation rule](https://www.xurrent.com/product-updates/introducing-automation-rules).

After preparing a reservation offering, the next step is to make sure that people can actually go to Xurrent Self Service to reserve one of the items.  To make this possible, a service desk manager can register a request template of the category ‘Reservation’.

The advantage of using a request template to make a reservation offering available is not only that the visibility can be set.  Request templates also make it possible to relate a change template to trigger a standard workflow for the selected reservation offerings.

Multiple reservation offerings can be selected in a request template of the category ‘Reservation’.  This makes it possible to, for example, add one reservation offering with the pool cars in Houston and another that has the pool cars in Chicago linked to it.  People in Chicago who are covered for the ‘Pool Cars Chicago’ service instance will then be able to use the same request template, but will only be able to reserve a car from the Chicago pool.

After saving the reservation request template, people who are covered for (one of) the service instance(s) of the reservation offerings linked to the request template can use Xurrent Self Service to make a reservation.

If they call the service desk, the service desk analyst who is taking the call will be able to do the same for the caller in the Service Desk console.

By selecting the reservation request, the user is presented with a calendar that shows all the reservations for the configuration items that the configuration manager linked to the reservation offering.

The filter icon is available above the list of items that can be reserved to make it possible to reduce this list to the items that meet certain criteria.

The small backward, forward, calendar, plus and minus icons in the upper right of the calendar allow the user to go backward or forward in time, jump to a specific date on the calendar, zoom in or zoom out.

After zooming in, it is possible to see the hours of a specific date.

The light-colored part on the left side of each horizontal bar that represents a reservation signifies that it is not possible to reserve the item during that time because it is being prepared for the reservation.  The length of this light-colored part is dictated by the value specified in the Preparation duration field of the reservation offering.

When the user clicks anywhere in one of the calendar’s rows, the first available time slot for the item in that row is selected.

The user can now drag the end of the reservation to specify the desired duration.  Clicking in the middle of the reservation allows its start to be moved backward or forward in time without changing its duration.  Once the time slot has been selected, the user can press ‘Continue’.

This opens the reservation request so that the user can enter a subject and an optional description before the request is saved.

After pressing the Save button, the user is able to add the reservation to her calendar.  The user also has the option to cancel the reservation.

Users can review their reservations by clicking on the ‘My Reservations’ option, which is now available in Xurrent Self Service.

Selecting the ‘My Reservations’ option opens a calendar in which all their past, current and upcoming reservations are visible.

In the Xurrent Specialist Interface, the request for the reservation that was submitted is available in the ‘All Requests’ view of the Records console.

As long as the request has the status ‘Reservation Pending’, it will not show up in anyone’s inbox.  If any work is required to prepare the reserved item, the request template would be related to a change template, which would have caused the status of the reservation request to be ‘Change Pending’, also keeping the request from becoming visible in the Inbox console.

The details of the reservation are not actually stored in the request.  They are stored in a reservation record.  All specialists can review the reservations, but only configuration managers and account administrators can edit them.  To look up the upcoming, active and past reservations, anyone who has access to the Xurrent Specialist Interface can go to the Records console and select the ‘Reservations’ option.

These people can also select the ‘People’ option in the Records console, select a person, and click on the **Actions** button in the toolbar to see the option ‘Reservation Calendar’.  This option is available when the selected person has at least one reservation that is still open or ended less than one month ago and which is registered in a Xurrent account that the user who clicked on the **Actions** button has the [Auditor, Specialist or Account Administrator](https://help.xurrent.com/help/roles/) role of.  Clicking on the ‘Reservation Calendar’ option opens the Reservation Calendar of the selected person.

Related blog posts:

[Recurring Reservations](https://www.xurrent.com/product-updates/recurring-reservations)

[Private reservations](https://www.xurrent.com/blog/private-reservations)

[Reservations Instructions](https://www.xurrent.com/product-updates/reservation-instructions)
