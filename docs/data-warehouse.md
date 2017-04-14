DomainMOD has a Data Warehouse framework built right into it, which allows you to import the data stored on your web server. Currently the only web servers that are supported are ones that run WHM/cPanel.

If your web server doesn't run WHM/cPanel, or you don't want to import your web server data into DomainMOD, you can ignore this section.

**NOTE:** Importing your web server(s) into the Data Warehouse will not modify any of your other DomainMOD data, nor any of the data on your web server.

Supported Data
--------------
The following WHM sections are currently supported, but our end goal is to have every piece of WHM information that can be retrieved via the API stored in the Data Warehouse.

**Accounts**  
Domain, IP Address, Owner, User, Contact Email, Plan, Theme, Shell, Partition, Disk Limit, Disk Usage, Max Addons, Max FTP Accounts, Max Email Lists, Max Parked Domains, Max POP Accounts, Max SQL Accounts, Max Subdomains, Creation Date, Suspend Status, Suspend Reason, Suspend Time, Max Email Per Hour, Failed Email % Before Defer, Min Failed Email # Before Defer

**DNS Zones**  
Zone Filename, Original/Primary Source of Zone Data, Admin Email, Serial #, Refresh, Retry, Expiry, Minimum TTL, Authoritative Name Server

**DNS Records**  
TTL, Class, Type, IP Address, CNAME, Mail Server, Mail Server Priority, TXT Data, Line # of Zone, # of Lines, RAW Data

Setup
-----
In order to use the Data Warehouse you first need to add your web server(s).

**Adding A Web Server**

1. Click on **Data Warehouse** on the main menu.

2. Click the **Manage Servers** button.

3. Click the **Add Web Server** button.

4. Enter your server's details and then click the **Add Server** button.

Building The Data Warehouse
---------------------------
Once you've added your web server(s), building your Data Warehouse is just a couple clicks away.

1. Click on **Data Warehouse** on the main menu.

2. Click the **Rebuild DW** button.

At this point your browser will build the Data Warehouse, which may take some time, and depending on how much data you have stored on your web server this process may timeout. Instead of building the Data Warehouse manually like this, we recommend that you setup the [cron job](getting-started.md#cron-job) that comes with DomainMOD, which will completely automate your Data Warehouse builds. 
