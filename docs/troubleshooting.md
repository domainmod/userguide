Installation
-----------
<h4>During installation the database tables are being created but some of the data isn't getting inserted.</h4>

MySQL strict mode may be enabled on your server. In order for DomainMOD to install and run, strict mode must to be disabled.

To disable strict mode you need to edit your MySQL configuration file. In it there will be a line that looks like:

**sql-mode="STRICT\_TRANS\_TABLES,NO\_AUTO\_CREATE\_USER,NO\_ENGINE\_SUBSTITUTION"**

To disable strict mode you need to remove STRICT\_TRANS\_TABLES from this line (including the comma after it, if there is one), which in this example would leave you with:

**sql-mode="NO\_AUTO\_CREATE\_USER,NO\_ENGINE\_SUBSTITUTION"**

Once disabled you will need to restart MySQL, and then DomainMOD should install properly.


<BR>Usage
-------------
<h4>DomainMOD seems to be working properly, but when I use the software I get a bunch of warning messages, such as "undefined index" and "undefined variable".</h4>

This is related to the error reporting level that you have turned on in PHP. Although these are only warnings and won't actually be breaking anything, you can get rid of them by editing your php.ini file and changing the error_reporting line.

Right now you probably have something that looks like this:

**error\_reporting = E\_ALL**

But you should have something that looks like this:

**error_reporting = E\_ALL & ~E\_NOTICE & ~E\_STRICT & ~E\_DEPRECATED**

Commented out in your php.ini file, above the error_reporting directive, there may be a suggested error reporting line for a "Production" environment. Try using that line instead of what you're using now, restart Apache/PHP, and that should get rid of the errors.


<h4>I'm trying to connect DomainMOD to my domain registrar account using the API so that I can import my domains, but everything in the Domain Queue just says "Pending".</h4> 

In order to import your domains using the domain registrar's API you must setup the [cron job](getting-started.md#cron-job) that comes with DomainMOD. In addition to having the cron job running, you must also have your API credential saved along with your registrar account Asset.


<h4>I've setup the Data Warehouse within DomainMOD, but none of my changes propagate to my web server.</h4>

The Data Warehouse is read-only. You can import data from your web server into your Data Warehouse, but this data is for informational purposes only, and you can't edit your server data within DomainMOD and have it update your web server. This is something that will be worked on in the future, but is currently not possible.
