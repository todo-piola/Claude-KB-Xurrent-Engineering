---
title: "Even More Accurate SLA Reporting"
date: "June 30, 2020"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/even-more-accurate-sla-reporting"
slug: "even-more-accurate-sla-reporting"
---

# Even More Accurate SLA Reporting

Xurrent is renowned for its SLA reporting.  Before each release, automated scripts test over 100 scenarios to ensure that even edge cases cannot negatively affect the accuracy of the SLA reports.

There is one edge case, however, that our industry has never bothered to solve.  It concerns the scenario where the clock is stopped for an incident and after the clock has started again, the impact of the incident is updated, causing the support hours used for the SLA target calculations to change.

The reason why this makes the target calculation so complex is best explained with a simple example.  Let’s assume that an end user sent an email to the service desk explaining that he is no longer able to use the SAP service and neither can his colleagues.  The service offering that dictates the targets of the SLA by which the user is covered has the following targets defined for high-impact and top-impact incidents:

The service desk analyst, who picked up the email and registered the new request, set the status to ‘Waiting for Customer’, causing the clock to be stopped.  This happened at 9am on Monday morning.  Because the end user indicated the service to be down for multiple users, the impact of the request was set to ‘Top’.  The [affected SLA](https://help.xurrent.com/help/affected_sla/) therefore looks like this:

When the end user responds exactly 7 days later, it turns out that the service is merely slow and people are still able to use it.  This prompts the service desk to update the impact level to ‘High’.

The clock was stopped for 7 days while the impact was ‘Top’.  Because the support hours for a top-impact incident are 24×7, the total stopped clock duration is 7 x 24 = 168 hours.  And because the impact was subsequently updated to ‘High’, the support hours have been reduced to 8 hours per day from Monday through Friday.  The affected SLA that is linked to the request now looks as follows:

Obviously, the new resolution target is too far in the future.  The maximum resolution duration for a high-impact SAP incident is only 40 support hours, which is exactly 1 week.  But when the stopped clock duration of 168 support hours is added, the new support hours are used to calculate the new target, which adds more than 4 weeks.

Xurrent now makes sure that it recalculates the stopped clock duration when the support hours of an affected SLA are updated.  To make this possible, Xurrent stores the start and end of each stopped clock duration.

A stopped clock period is captured when:

- the status of a request was set to ‘Waiting for Customer’ and the customer has responded,
- a request was initially thought to be related to an incorrect service instance, but later it turned out to be the correct service instance after all,
- a request was completed, but was later reopened.

People who are looking at an affected SLA record of a request will now notice that each stopped clock period is shown. It is these stopped clock periods that allow the stopped clock duration to be corrected after a different support hours calendar is applied to an affected SLA.

To fully appreciate the quality of the calculations for these more exceptional scenarios, give this use case a try in a Xurrent trial instance.  Then do the same in another service management solution to see the difference.
