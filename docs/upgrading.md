**WARNING:** Before upgrading it's strongly recommended that you make a backup of your DomainMOD installation directory and database. If something goes wrong during the upgrade there may be no way to recover your data, and having a backup of your installation directory and database will allow you to easily restore your previous installation.

**Upgrade Option #1**  
If you installed DomainMOD by downloading the .ZIP file, visit the following URL to download the most up-to-date version: <https://domainmod.org/download/>

Once the download completes, upload and unpack the new archive overtop of where you installed the previous version (or unpack it and then upload it, whichever you prefer).

**Upgrade Option #2**  
If you installed DomainMOD using git right from your web server, just run the following command from within your installation directory to upgrade:

    git pull
    
That's it! Upgrading with git is very easy, which is one of the reasons it's our recommended method for obtaining the DomainMOD source code.
