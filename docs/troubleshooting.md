Installation
------------
<a name="strictmode"></a><h4>I get a blank page and can't go any further OR I get an Error 500 OR The database tables are being created but some of the data isn't getting inserted.</h4>

MySQL strict mode may be enabled on your server. In order for DomainMOD to install and run, strict mode must to be disabled.

To disable strict mode you need to edit your MySQL configuration file. In it there will be a line that looks like:

    sql-mode="STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

To disable strict mode you need to remove STRICT\_TRANS\_TABLES from this line (including the comma after it, if there is one), which in this example would leave you with:

    sql-mode="NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

Once disabled you will need to restart MySQL, and then DomainMOD should install properly.

!!! note
    As of v4.11, DomainMOD will try to disable strict mode automatically during the database connection, but if you're still experiencing issues you should follow the steps above.

<h4>The images and CSS are broken or you're receiving an error that there are too many redirects.</h4>

This is generally caused by an invalid web root in your config.inc.php file. Please double check your config.inc.php file and confirm that the $web_root variable reflects the directory where you installed DomainMOD.

For example, if you access DomainMOD via the URL http://example.com/domains/ the $web_root variable should be:

    $web_root = "/domains"; (don't include a trailing slash!)

And if you've installed DomainMOD in the root folder of a domain or subdomain, the $web_root variable in your config.inc.php file should be blank, like so:

    $web_root = "";


<BR>Upgrading
-------------
<h4>There was an issue while upgrading and now I can't access DomainMOD.</h4>

Although we personally haven't see this happen yet, it's definitely possible. This is why we recommend you backup your DomainMOD installation directory and database before upgrading (you did make that backup, right?).

Follow these steps to restore your copy of DomainMOD:

1. Restore your DomainMOD database backup to the same location as your previous DomainMOD database.

2. Instead of logging into DomainMOD to upgrade your database, run the below script from the command line.

    \[FULL SERVER PATH TO DOMAINMOD\]/update.php
    
    The full command will look something like this, depending on the location of PHP and DomainMOD on your server:
    
    /usr/bin/php -f /home/user/www/domainmod/update.php

3. If you receive a notice that your upgrade was **successful**, switch back to your web browser and try to login to DomainMOD. If you're able to login successfully you can ignore the rest of these steps.

4. If you receive a notice that your upgrade was **unsuccessful**, keep a record of any error messages that are displayed and proceed to the next step.

4. Restore your DomainMOD database backup again, then [download the previous version that you were using](https://github.com/domainmod/domainmod/releases) and go through the standard installation steps, pointing it at your newly-restored database in the config.inc.php file. This should get you back to where you were before you tried upgrading.

5. Contact us with any error messages that were displayed and we'll try to help figure out what went wrong with your upgrade.


<BR>Usage
---------
<a name="errorlevel"></a><h4>DomainMOD seems to be working properly, but when I use the software I get a bunch of warning messages, such as "undefined index" and "undefined variable".</h4>

This is related to the error reporting level that you have turned on in PHP. Although these are only warnings and won't actually be breaking anything, you can get rid of them by editing your php.ini file and changing the error_reporting line.

Right now you probably have something that looks like this:

    error_reporting = E_ALL

But you should have something that looks like this:

    error_reporting = E_ALL & ~E_NOTICE & ~E_STRICT & ~E_DEPRECATED

Commented out in your php.ini file, above the error_reporting directive, there may be a suggested error reporting line for a "Production" environment. Try using that line instead of what you're using now, restart Apache/PHP, and that should get rid of the errors.


<h4>I'm trying to connect DomainMOD to my domain registrar account using the API so that I can import my domains, but everything in the Domain Queue just says "Pending".</h4> 

In order to import your domains using the domain registrar's API you must setup the [cron job](getting-started.md#cron-job) that comes with DomainMOD. In addition to having the cron job running, you must also have your API credential saved along with your registrar account Asset.


<h4>I've setup the Data Warehouse within DomainMOD, but none of my changes propagate to my web server.</h4>

The Data Warehouse is read-only. You can import data from your web server into your Data Warehouse, but this data is for informational purposes only, and you can't edit your server data within DomainMOD and have it update your web server. This is something that will be worked on in the future, but is currently not possible.


<h4>I'm getting the error, "Database Connection Error: 1045".</h4>

Error 1045 is an access denied error, which seems to be caused when the user doesn't have appropriate permissions on the database, or there's another privilege issue with the database. Unfortunately this is pretty difficult to troubleshoot on our end, as there are many things that can cause this.

We would recommend trying some of the suggestions for this error in Google and see if any of them help: [https://www.google.com/search?q=Database+Connection+Error%3A+1045](https://www.google.com/search?q=Database+Connection+Error%3A+1045).


<h4>I'm trying to import data using the Domain Queue, but everything is stuck on "Processing".</h4>

In case there's an issue with the cron job you can also try triggering the queue manually. Go to Administration -> Task Scheduler, and then beside "Domain Queue Processing" click the "run now" link (this may take a bit of time to run). Then go back to the queue and see if anything has changed.

If that doesn't work you can try clearing the queue items that are currently processing by going to Administration -> Maintenance, and then clicking on "Clear Queue Processing". Now try the last suggestion again to see if running the queue manually through the Task Scheduler helps.

If that still doesn't do it go to Administration -> Maintenance, and then click on "Clear Queues". This will completely clear out the queue. Now try retrieving your data again using the Domain Queue.

<a name="javascript"></a><h4>Form fields aren't displaying properly, such as checkboxes and text fields showing as empty boxes.</h4>

This is usually caused by JavaScript being disabled in your web browser. If enabling JavaScript doesn't fix the issue try disabling any ad blockers or other content blockers you may have installed.

<BR>Debugging
-------------
If you're still having issues you can enable Debugging Mode, which will make DomainMOD start logging your actions and errors, which can help us troubleshoot your issue.

!!! note
    No sensitive information gets stored in the debugging log. Passwords, API keys, and other sensitive information is replaced with asterisks, so we will never be able to view your private data.
 
To enable Debugging Mode:

1. Click **Administration** on the main menu, then click **System Settings**.

2. Change the **Debugging Mode** option to **Enabled**.

3. Click the **Update System Settings** button.

Once debugging is enabled use DomainMOD as you normally would, repeating the steps you took when you first encountered the issue. Once you've done this continue with the below steps.

1. If you haven't already, visit the DomainMOD [support forum](https://domainmod.org/forum/) or [issue tracker](https://domainmod.org/issues/) and post about your issue.

2. In DomainMOD, click on **Administration** and then **Debug Log**.

3. Click the **Export** button to export the debugging log.

In addition to the debugging log you should also retrieve your PHP error log, which will give us additional information about your issue.

To find the location of your PHP error log:

1. In DomainMOD, click on **Administration** and then **System Information**.

2. Look for the heading named **PHP Error Log Location**. This will show you the location of the PHP error log on your web server.

Once you have both your debugging log and PHP error log send an email to <debugging@domainmod.org> and attach the log files. Please also include the URL to your support forum post or issue tracker ticket so that we can determine the issue you're contacting us about.

We will review your logs and get back to you as soon as we can!

Also, if you haven't already, make sure you disable Debugging Mode.
