Custom Fields
-------------

Custom Fields help extend the functionality of DomainMOD by allowing the user to create their own data fields. For example, if you wanted to keep track of which domains are currently setup in your Analytics software, you could create a new Analytics check box field and start tracking this information for each of your domains. Combine Custom Fields with the ability to update them with the [Bulk Updater](bulk-updater.md)*, and the sky's the limit in regards to what data you can easily track!

When you export your domain or SSL certificate data, the information contained in your custom fields will automatically be included in the exported data.

**Custom Field Types:** Check Box, Date, Text Field, Text Area, Time Stamp, URL

!!! note
    As of v4.13, DomainMOD has the ability to display your Custom Field data on the main Domain and SSL Certificate pages.

!!! note
    \* The Bulk Updater currently only allows you to update Custom Domain Fields, but not Custom SSL Certificate Fields.

Task Scheduler
--------------
The Task Scheduler (**Administration** -> **Task Scheduler**) runs DomainMOD's system jobs, such as processing the Domain Queue, sending expiration emails, and building the Data Warehouse. In order for it to work, you must set up the [cron job](getting-started.md#cron-job) that comes with DomainMOD, and you can also limit who can run it with a [Task Scheduler Key](getting-started.md#task-scheduler-key).

As of v4.25.0, each daily task runs at the same local time all year, including across daylight saving time changes. When you set a daily task's run time, it's saved in your own time zone (from your user settings), and the Task Scheduler page shows each daily task's run time along with its time zone. Changing your time zone later doesn't move tasks that are already set, so set their run times again if you want them to follow your new time zone. When you upgrade to v4.25.0, existing daily tasks keep running at the same moment, using the time zone of the user who installed DomainMOD (or of the first administrator).
