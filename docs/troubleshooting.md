Installation
-----------
<h4>During installation the database tables are being created but some of the data isn't getting inserted.</h4>

MySQL strict mode may be enabled on your server. In order for DomainMOD to install and run, strict mode must to be disabled.

To disable strict mode you need to edit your MySQL configuration file. In it there will be a line that looks like:

    sql-mode="STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

To disable strict mode you need to remove STRICT\_TRANS\_TABLES from this line (including the comma after it, if there is one), which in this example would leave you with:

    sql-mode="NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

Once disabled you will need to restart MySQL, and then DomainMOD should install properly.

<h4>The images and CSS are broken or you're receiving an error that there are too many redirects.</h4>

This is generally caused by an invalid web root in your config.inc.php file. Please double check your config.inc.php file and confirm that the $web_root variable reflects the directory where you installed DomainMOD.

For example, if you access DomainMOD via the URL http://example.com/domains/ the $web_root variable should be:

    $web_root = "/domains"; (don't include a trailing slash!)

And if you've installed DomainMOD in the root folder of a domain or subdomain, the $web_root variable in your config.inc.php file should be blank, like so:

    $web_root = "";


<BR>Upgrading
-----------
<h4>There was a problem while upgrading and now I can't access DomainMOD.</h4>

Although we personally haven't see this happen yet, it's definitely possible. This is why we recommend you make a backup of your entire DomainMOD database before upgrading (you did make that backup, right?).

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
-------------
<h4>DomainMOD seems to be working properly, but when I use the software I get a bunch of warning messages, such as "undefined index" and "undefined variable".</h4>

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

In case there's a problem with the cron job you can also try triggering the queue manually. Go to Administration -> Task Scheduler, and then beside "Domain Queue Processing" click on the "run now" link (this may take a bit of time to run). Then go back to the queue and see if anything has changed.

If that doesn't work you can try clearing the queue items that are currently processing by going to Administration -> Maintenance, and then clicking on "Clear Queue Processing". Now try the last suggestion again to see if running the queue manually through the Task Scheduler helps.

If that still doesn't do it go to Administration -> Maintenance, and then click on "Clear Queues". This will completely clear out the queue. Now try retrieving your data again using the Domain Queue.
