As of v4.14, DomainMOD has a Backup & Restore utility. This feature enables you to perform complete backups and restores of your DomainMOD database. This allows you to export your entire system in a single file so that it can easily be backed up and/or restored, which is helpful if you want to perform regular backups of your data, you need to move DomainMOD to a new server, or you want to change your installation method.

This process backs up the data saved in your database. If you also want to save your database connection information, you should backup your /_includes/config.inc.php file.


!!! note "Note"
    Before you can use Backup & Restore you must update the permissions on the /var/www/html/domainmod/temp folder ("_chmod 777 /var/www/html/domainmod/temp_"). If you're unsure how to do this your web hosting provider should be able to assist you.
    
    The above path (/var/www/html/domainmod/temp) will need to be modified for your specific web server and DomainMOD installation location.



Backup
------
To backup your DomainMOD database:

1. Login to DomainMOD as an administrator

2. Navigate to **Administration** -> **Backup & Restore**

3. In the **Backup** section, click the **Backup Entire Database** button

4. At this point you will be prompted to download the file domainmod-backup.sql, which contains a copy of your entire database

Restore
------

!!! danger "Warning"
    Before restoring your DomainMOD database, ensure that you're restoring a database that is of the same version as the software that you're restoring it to. For example, if you were using DomainMOD v4.14 when you backed up your database, you must restore that database to an installation of DomainMOD v4.14.  
To restore your DomainMOD database:

1. Login to DomainMOD as an administrator

2. Navigate to **Administration** -> **Backup & Restore**

3. In the **Restore** section, click the **Choose File** button and then select the domainmod-backup.sql file that you want to restore

4. Click the **Restore Entire Database** button

5. Once the restore is complete you will automatically be logged out of DomainMOD. You should now be able to login using the accounts that you just restored.

Migrating
------
{!_migrating.md!}
