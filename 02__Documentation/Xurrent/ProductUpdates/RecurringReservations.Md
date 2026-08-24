---
title: "Recurring Reservations"
date: "December 20, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/recurring-reservations"
slug: "recurring-reservations"
---

# Recurring Reservations

In Xurrent, users can make [reservations](https://www.xurrent.com/product-updates/introducing-reservations)for configuration items by submitting a request from a request template of the category ‘Reservation’.  This functionality has now been extended by offering the possibility to book recurring reservations.  For an organization to allow recurring reservations, the new `Allow repeat` box in the corresponding reservation offering must be ticked.

Reservation offerings are used to define which configuration items (CIs) can be made available for people to reserve for temporary use, when, and for how long.  When the ‘Allow repeat’ option is selected, the `Initial status`field is set to ‘Confirmed’ and the `Min. advance duration` field is cleared.  The `Max. advance duration` field now also defines until when the recurring reservations will be scheduled, and must be set to a value between 1 day and 1 year.  Although the value of this field is displayed in hours, it may also be set by entering ‘1d’ or ‘4w’, for example, to indicate a duration of 1 day or 4 weeks respectively.

Creating a reservation has not changed.  After choosing a request template of the category ‘Reservation’, the user is asked to select a timeslot for the desired configuration item.  In the example below the selected CI is one of the Xurrent Demo environments.

Next, the reservation request is opened in Edit mode, where the user can choose to make the reservation recurring by selecting the desired option from the `Repeats`field.  The first three options after ‘No repeat’ are suggestions based on the chosen date.  So if the first reservation is made for a Friday, one of the suggestions will be ‘Weekly on Fridays’.  When selecting ‘Custom…’ the user can decide exactly when and until when the reservations are made.

After saving, the reservations can be found in the ‘Reservations’ section of the Records console, where a new filter has been created for the Reservations views to allow users to filter on recurring reservations.  The **Add to Calendar** button now downloads an iCalendar file (.ics) to add the whole series of reservations to the user’s preferred calendar.  When there is a conflict with another future reservation, an email is sent to the user with the details of that conflict.

In Self Service, users can manage their recurring reservations by navigating to ‘My reservations’ and selecting an occurrence of their reservation.  After modifying the reservation, the user is asked if only the selected occurrence should change, or also the already planned reservations in the future.

All new fields introduced with this enhancement are also supported by GraphQL and REST APIs and import/export.
