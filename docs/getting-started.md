Project Home: <https://domainmod.org>  
Project Demo: <https://demo.domainmod.org>  
Documentation: <https://domainmod.org/docs/>  
Source Code: <https://domainmod.org/source/>

About
-----
DomainMOD is an open source application written in PHP & MySQL used to manage your domains and other internet assets in a central location. DomainMOD also includes a Data Warehouse framework that allows you to import your web server data so that you can view, export, and report on your live data. Currently the Data Warehouse only supports web servers running WHM/cPanel.

Live Demo
---------
Not sure if DomainMOD is what you're looking for? Don't want to take the time to install it only to find out that it's not? We hate when that happens ourselves, which is why we've setup a live demo so you don't waste your time.

So go ahead, take the live demo for a test drive before you install: <https://demo.domainmod.org>

Requirements
------------
**Software**: PHP v5.3.2+, MySQL  
**PHP Extensions**: PDO (MySQL), cURL, OpenSSL  
**PHP Settings**: allow_url_fopen  

Downloading
-----------
There are currently three options for downloading DomainMOD.

**Option #1**  
Visit the following URL to download DomainMOD in a .ZIP file: <https://domainmod.org/download/>

**Option #2**  
Use git from your web server to retrieve the DomainMOD source code. To do so, change to the directory where you want to install DomainMOD and run the following command (this download option requires that you have git installed on your web server):

    git clone https://github.com/domainmod/domainmod.git

**Option #3**  
Use Softaculous from your web server to download **and** install DomainMOD.  Softaculous is the web hosting industry's leading software auto-installer, and it has helped millions of users install applications with a few clicks of a mouse. Softaculous easily integrates into the leading control panels like cPanel, Plesk, DirectAdmin, InterWorx, H-Sphere, and more. Check your hosting control panel or contact your web host if you're not sure if they offer Softaculous.

To install DomainMOD simply open Softaculous, use the search feature to find DomainMOD, and then click the "Install Now" button. After you answer a few questions about your installation Softaculous will do the rest.

More Information: <http://www.softaculous.com/softaculous/apps/others/DomainMOD/>

Installing
----------
If you installed DomainMOD using Softaculous in the previous step you can ignore the rest of this *Installing* section, as you should already have DomainMOD up-and-running.

If you downloaded the .ZIP file in the previous step, you will now need to upload the archive to your web server and then unpack it into the folder where you wish to install (or unpack it and then upload it, whichever you prefer).

If you used git to retrieve the source code in the previous step, just change to the directory where you ran the git command and your files are already waiting for you in a folder called /domainmod/. Feel free to rename this folder to whatever you want.

**Installation Steps**

1. Create a MySQL database that will be used to store DomainMOD's data.

2. In the '_includes' folder, copy config.SAMPLE.inc.php to config.inc.php and then update config.inc.php to reflect your web server's settings.

3. In a web browser, visit the URL where you just installed DomainMOD, enter the requested information, and then click the Install button. For example, example.com/domainmod/. After a few seconds a message will appear letting you know that the installation was successful.

4. Setup the below cron job on your web server.

Cron Job
--------
DomainMOD includes a Task Scheduler that allows you to run various system jobs at specified times, which helps keep your DomainMOD installation up-to-date and running smoothly, as well as notifies you of important information, such as emailing you to let you know about upcoming Domain & SSL Certificate expirations.

The Task Scheduler is very powerful, and it enables features that you otherwise wouldn't be able to use, but in order for it to function you need to schedule the below cron job to run on your web server. Once the cron job is setup to run the Task Scheduler will be live.

Filename: /cron.php

!!! note
    This file should be executed every 10 minutes.

Security
--------
Although we've done our best to secure DomainMOD, unfortunately there are many factors that could cause security holes, such as the software being run on insecure hardware, software like PHP and MySQL having out-of-date versions with known vulnerabilities, easy-to-guess passwords being used, and so on. Due to these factors we recommend the following steps to help secure your DomainMOD installation.

1. Do not use easy-to-guess passwords. **Ever**.

2. Although DomainMOD has its own authentication system, we recommend that you also use HTTP authentication on your installation folder to add an extra layer of security.

3. Do not store your account passwords or API keys in DomainMOD. Although the ability to save this information exists, **use it at your own risk**. This information is fairly secure if you run DomainMOD on your local computer, but there's a much higher risk of someone gaining access to it if you host the site on a server that is accessible to the outside world.

    !!! danger "Warning"
        Saving your API keys (and other relevant API connection information) in DomainMOD is necessary if you want to use the [Domain Queue](domain-queue.md), however we recommend that you only save this information temporarily while you're using the Domain Queue, and that you remove it as soon as you're done.

4. Do not host DomainMOD on a public website or on an easy-to-guess URL.

5. Do not give the URL to anyone who does not need to access DomainMOD. You should treat the URL like a password.

6. Always use the most up-to-date version of DomainMOD. This will help protect you from any security vulnerabilities that are found and fixed.

First Run
---------
After you've installed DomainMOD you should go through the [First Run](first-run.md) section to finish getting the software ready to use.
