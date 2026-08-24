# Knowledge Articles Import

Knowledge Articles can be imported into Xurrent using [UTF-8](http://en.wikipedia.org/wiki/Utf-8) or [UTF-16LE](https://en.wikipedia.org/wiki/UTF-16) encoded [comma-separated values (CSV)](http://en.wikipedia.org/wiki/Comma-separated_values) or [tab-separated values (TSV)](http://en.wikipedia.org/wiki/Tab-separated_values) files.

Detailed information about the data that can be specified in the columns of a Knowledge Articles import file can be found in [Knowledge Articles API - Fields](../../knowledge_articles.html#fields).

## CSV Example

```
Source,Source ID,Status,Internal Specialists,Covered Specialists,Key Contacts,End Users,Service,Service Instances,Subject,Description,Instructions,Created By,Created At,Updated At,Keywords
,,validated,1,1,1,1,Conference Room,"",How to book a conference room,Booking a conference room is easy. This article describes how you can do this using Outlook.,"To book a conference room, follow the step below:

1. Open the **Calendar** section in Outlook.
2. Open a new meeting.
3. In the **To** field, select the attendees along with the desired conference room.
4. Sent the meeting to the invitees.

As soon as the conference room has been confirmed, you will receive an email indicating that the conference room has accepted the meeting invitation.",joseph.coleman@widget.com @widget,2019-10-16T08:24:59-05:00,2019-10-16T08:24:59-05:00,"booking,schedule,scheduling"
,,validated,1,1,1,1,Personal Computing,"",How to connect a 2nd monitor to a desktop PC,"More and more people use two monitors to help them be more efficient. If you already have a two monitors, this article explains how you can hook both of them up to your computer.","To connect a second monitor to a desktop personal computer, follow the step below:

1. Plug the cable of the 2nd monitor in the 2nd VGA port on the back of your personal computer
2. Ensure the monitors are plugged into the electrical outlets and turn the computer and both monitors on.
3. Typically when your PC boots up, it may indicate that they have found new hardware. Follow the instructions for installing the drivers for your monitors or video card hardware. In many cases you may not need to install any drivers because many monitors may work with generic Windows drivers.
4. Once your PC has booted up, you may notice that both monitors are displaying the same information. You can change this by changing the video setting as follows:
1. Click **Start**, **Control Panel** Double-click **Display** to open the Display Properties window.
2. Click the **Settings** tab.
3. There should be two boxes with the number 1 and 2. Click the box displaying #2, then check the box that says ""Extend my Windows desktop onto this monitor"".
4. Click **Apply** to ensure that you have the monitor set the way you like, then click **OK**.
5. Ensure that you have the monitors set to the same resolution.",joseph.coleman@widget.com @widget,2019-10-16T08:25:00-05:00,2019-10-16T08:25:00-05:00,screen
```

[download CSV](https://developer.xurrent.com/csv/knowledge_articles.csv)
