The below steps walk you through how to migrate DomainMOD to a new server.

!!! danger "Warning"
    Before migrating it's **strongly** recommended that you backup your DomainMOD installation directory and database. If something goes wrong during the migration process there may be no way to recover your data, and having a backup of your installation directory and database will allow you to easily restore your data.
 
1. [Upgrade](https://domainmod.org/docs/userguide/upgrading/) to the newest version of DomainMOD. **Don't go any further with the migration steps until you've upgraded and everything is working properly.**

2. Export a copy of your DomainMOD database (using mysqldump, phpMyAdmin, etc.). 

3. On your new server, create a database and import the old DomainMOD database that you exported in step #2.

4. On your new server, [download and install](https://domainmod.org/docs/userguide/getting-started/#downloading) the newest version of DomainMOD. During installation, when updating the database details in the /_includes/config.inc.php file, be sure to use the new database details from step #3.

5. That's it! You should now have full access to your old DomainMOD data on your new server.