!!! danger "Warning"
    Before migrating it's **strongly** recommended that you backup your DomainMOD installation directory and database. If something goes wrong during the migration process there may be no way to recover your data, and having a backup of your installation directory and database will allow you to easily restore your data. 
        
    The Backup & Restore instructions can be found [here](backup-restore.md).

To migrate your DomainMOD installation from one server to another:

1. [Old Server] [Upgrade to the newest version of DomainMOD](https://domainmod.org/docs/userguide/upgrading/)

2. [Old Server] Export a copy of your DomainMOD database using the above **Backup** feature

3. [New Server] [Download and install the newest version of DomainMOD](https://domainmod.org/docs/userguide/getting-started/#downloading)

4. [New Server] Login to DomainMOD and navigate to **Administration** -> **Backup & Restore**

5. [New Server] In the **Restore** section, click the **Choose File** button and then select the domainmod-backup.sql file that you want to restore

6. [New Server] Click the **Restore Entire Database** button

7. [New Server] Once the restore is complete you will automatically be logged out of DomainMOD. You should now be able to login using the accounts that you just restored.

8. That's it! DomainMOD has now been migrated to your new server.
