Installation
------------
<a name="strictmode"></a><h4>
The database tables are being created but some of the data isn't getting inserted
I get a blank page and can't go any further  
I get an "Error 500" message  
</h4>

MySQL strict mode may be enabled on your server. In order for DomainMOD to install and run, strict mode must to be disabled.

To disable strict mode you need to edit your MySQL configuration file. In it there will be a line that looks like:

    sql-mode="STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

To disable strict mode you need to remove STRICT\_TRANS\_TABLES from this line (including the comma after it, if there is one), which in this example would leave you with:

    sql-mode="NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

Once disabled you will need to restart MySQL, and then DomainMOD should install properly.

!!! note
    As of v4.11, DomainMOD will try to disable strict mode automatically during the database connection, but if you're still experiencing issues you should follow the steps above.

<a name="webroot"></a><h4>
I'm receiving an error that there are too many redirects  
The images and CSS are broken  
</h4>

This is generally caused by an invalid web root in your config.inc.php file. Please double check your config.inc.php file and confirm that the $web_root variable reflects the directory where you installed DomainMOD.

For example, if you access DomainMOD via the URL http://example.com/domains/ the $web_root variable should be:

    $web_root = "/domains"; (don't include a trailing slash!)

And if you've installed DomainMOD in the root folder of a domain or subdomain, the $web_root variable in your config.inc.php file should be blank, like so:

    $web_root = "";


<BR>Upgrading
-------------
<a name="upgrading"></a><h4>
There was an issue while upgrading and now I can't access DomainMOD
</h4>

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
<a name="errorlevel"></a><h4>
The software seems to be working properly, but some messages are being displayed, such as "*undefined index*" and "*undefined variable*"
</h4>

This is related to the error reporting level that you have turned on in PHP. Although these are only warnings and won't actually be breaking anything, you can get rid of them by editing your php.ini file and changing the error_reporting line.

Right now you probably have something that looks like this:

    error_reporting = E_ALL

But you should have something that looks like this:

    error_reporting = E_ALL & ~E_NOTICE & ~E_DEPRECATED

If your current line includes `~E_STRICT`, you can remove it. PHP 8 never raises E_STRICT, and PHP 8.4 deprecated the constant.

Commented out in your php.ini file, above the error_reporting directive, there may be a suggested error reporting line for a "Production" environment. Try using that line instead of what you're using now, restart Apache/PHP, and that should get rid of the errors.


<a name="pending"></a><h4>
I'm trying to connect DomainMOD to my domain registrar account using the API so that I can import my domains, but everything in the Domain Queue just says "Pending"
</h4> 

In order to import your domains using the domain registrar's API you must set up the [cron job](getting-started.md#cron-job) that comes with DomainMOD. In addition to having the cron job running, you must also have your API credential saved along with your registrar account Asset. (Domains you [add without an API](domain-queue.md#rdap) don't need any API credentials, but they still need the cron job.)


<a name="processing"></a><h4>
I'm trying to import data using the Domain Queue, but everything is stuck on "Processing"
</h4>

In case there's an issue with the cron job you can also try triggering the queue manually. Go to *Administration -> Task Scheduler*, and then beside "Domain Queue Processing" click the "run now" link (this may take a bit of time to run). Then go back to the queue and see if anything has changed.

If that doesn't work you can try clearing the queue items that are currently processing by going to *Administration -> Maintenance*, and then clicking on "Clear Queue Processing". Now try the last suggestion again to see if running the queue manually through the Task Scheduler helps.

If that still doesn't do it go to *Administration -> Maintenance*, and then click on "Clear Queues". This will completely clear out the queue. Now try retrieving your data again using the Domain Queue.

<a name="dwprop"></a><h4>
I've setup the Data Warehouse within DomainMOD, but none of my changes propagate to my web server
</h4>

The Data Warehouse is read-only. You can import data from your web server into your Data Warehouse, but this data is for informational purposes only, and you can't edit your server data within DomainMOD and have it update your web server. This is something that will be worked on in the future, but is currently not possible.


<a name="sslverify"></a><h4>
After upgrading, I'm getting the error "Unable to verify the SSL certificate of a remote server"
</h4>

As of v4.24.02, DomainMOD checks the SSL certificate of every server it connects to, such as your registrars' APIs, your Data Warehouse servers, and the update check. This error means a server's certificate couldn't be verified, so DomainMOD didn't connect to it. The error names the service and includes the cURL error, which can help narrow down the cause.

To fix it:

1. Check that your server's date and time are correct. If the clock is wrong, valid certificates can look expired.

2. Update your operating system's CA certificates (on most Linux systems this is the **ca-certificates** package).

3. If `curl.cainfo`, `openssl.cafile`, or `openssl.capath` in your php.ini points to a file or folder that's missing or out of date, fix the path or remove the setting, then restart Apache/PHP.

4. If your server connects to the internet through a proxy that inspects HTTPS traffic, add the proxy's CA certificate to your server's trusted certificates.

If the error is for a Data Warehouse server with a self-signed certificate, the best fix is to give that server a valid certificate, or to add its certificate (or the CA that signed it) to your DomainMOD server's trusted CA certificates. As a last resort, if you connect to it over a network you trust, you can switch off **Verify SSL Certificate?** for that server only (see [Data Warehouse Setup](data-warehouse.md#setup)). With it off, DomainMOD can't tell whether it's talking to your real server, so anyone able to intercept the connection could see your WHM API Token or Remote Access Key.

If you see "Unable to connect to a remote server" instead, DomainMOD couldn't reach the server, so check your server's network connection and firewall. "A remote server didn't respond in time" means the server took too long to connect or answer, so check that the remote service is up and that your server can reach it, then try again.


<a name="dberr1045"></a><h4>
I'm getting the error, "Database Connection Error: 1045"
</h4>

Error 1045 is an access denied error, which seems to be caused when the user doesn't have appropriate permissions on the database, or there's another privilege issue with the database. Unfortunately this is pretty difficult to troubleshoot on our end, as there are many things that can cause this.

We would recommend trying some of the suggestions for this error in Google and see if any of them help: [https://www.google.com/search?q=Database+Connection+Error%3A+1045](https://www.google.com/search?q=Database+Connection+Error%3A+1045).


<a name="javascript"></a><h4>
Form fields aren't displaying properly, such as checkboxes and text fields showing as empty boxes
</h4>

This is usually caused by JavaScript being disabled in your web browser. If enabling JavaScript doesn't fix the issue try disabling any ad blockers or other content blockers you may have installed.

<a name="currency"></a><h4>
The currency conversions aren't working properly  
My fees are all showing up as zero
</h4>

This is usually caused by a currency converter that's experiencing downtime. You can fix this by changing the currency conversion source.

1. Click **Administration** on the main menu, then click **System Settings**.

2. Click on the **Currency Converter** dropdown menu and choose a new source.

3. Click the **Update System Settings** button. 

After the Currency Converter source has been changed you can force a currency conversion update by going to *Administration -> Task Scheduler*, and then clicking the "run now" link beside "Update Conversion Rates".

<BR>Debugging
-------------
If you're still having issues you can enable Debugging Mode, which will make DomainMOD start logging your actions and errors, which can help us troubleshoot your issue.

!!! note
    No sensitive information gets stored in the debugging log. Passwords, API keys, and other sensitive information is replaced with asterisks, so we will never be able to view your private data.
 
To enable Debugging Mode:

1. Click **Administration** on the main menu, then click **System Settings**.

2. Turn on the **Debugging Mode** switch.

3. Click the **Update System Settings** button.

Once debugging is enabled use DomainMOD as you normally would, repeating the steps you took when you first encountered the issue. Once you've done this continue with the below steps.

1. If you haven't already, post about your issue in the [Support Portal](https://support.domainmod.org). If you're a developer and you've found a bug you can point to in the code, you can open an issue on [GitHub](https://github.com/domainmod/domainmod/issues) instead.

2. In DomainMOD, click on **Administration** and then **Debug Log**.

3. Click the **Export** button to export the debugging log.

In addition to the debugging log you should also retrieve your PHP error log, which will give us additional information about your issue.

To find the location of your PHP error log:

1. In DomainMOD, click on **Administration** and then **System Information**.

2. Look for the heading named **PHP Error Log Location**. This will show you the location of the PHP error log on your web server.

Once you have both your debugging log and PHP error log send an email to <debugging@domainmod.org> and attach the log files. Please also include the URL to your Support Portal post or GitHub issue so that we can determine the issue you're contacting us about.

We will review your logs and get back to you as soon as we can!

Also, if you haven't already, make sure you disable Debugging Mode.

<BR>Helper Programs
-------------------
If all else fails, DomainMOD has some "helper" programs that support can supply you with in order to help investigate or fix your issue. Helper programs are nothing more than simple scripts that can perform actions on your DomainMOD installation, whether it's performing an update on your database or setting a temporary variable.

Although helpers are generally custom and specific to the user's issue, we wanted to include a generic helper publicly so that users could get a feel for what helpers are and what they do.

In DomainMOD v4.18, we implemented strict [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) headers in order to help secure the application and reduce the risk of certain web-based attacks. We also enabled forced HTTPS, which ensures that your DomainMOD installation will **only** work if you've secured your web hosting with an SSL certificate.

Although we highly recommend keeping the CSP headers enabled, as well as using an SSL certificate to secure your DomainMOD installation, we realize that some users may not always be able to have these features enabled. If you're one of those users, and you need to disable CSP and HTTPS, you could use the below helper to do so.

You would simply create the file */helpers/top.php* and paste the below contents into it. That's all there is to it! The next time your visit your DomainMOD installation CSP and forced HTTPS will both be disabled.

````
<?php
// Contents of: /helpers/top.php
$disable_csp = 1;
$force_https = 0;
````

!!! danger "Warning"
    If you're using a helper to investigate or fix something, and the helper is only intended to be used temporarily, don't forget to delete the helper file as soon as you're done using it!     
