The easiest option for adding domains is to use the Domain Queue, which allows you to supply a list of domains and let DomainMOD take care of the rest (and in some cases you don't even need to supply the list of domains, it will be automatically retrieved from your registrar account).

This option uses your domain registrar's API to retrieve information required to add domains, so unfortunately it only works if your registrar has an API and support for it has been built into DomainMOD. **Before using this option make sure your API credentials have been saved with your registrar account.**

**NOTE:** In order to use the Domain Queue you must first [setup the cron job](getting-started.md#cron-job) that comes with DomainMOD.

Supported Registrars
----------------------
The following registrars are currently supported by the Domain Queue:

Above.com, DNSimple, DreamHost, Dynadot, eNom, Fabulous, Freenom (Reseller Accounts Only), GoDaddy, Internet.bs, Name.com, NameBright, Namecheap, NameSilo, OpenSRS, ResellerClub

Usage
-------
1. Click on **Domains** on the main menu.

2. Click the **Add Domains To Queue** button on the Domains page.

3. On the dropdown list, choose the registrar account that you would like to import using the Domain Queue.

4. If requested, paste in a list of the domains you want to add to the Domain Queue. This is not always required, as some domain registrars will retrieve the list of domains from your account automatically.

5. Click the **Add Domains** button.

6. You will now be taken to the Domain Queue page, where you can see the status of your domain imports. You can also access the Domain Queue by clicking on **Queue** on the main menu (this menu option is only available when you have domains being processed in the queue).

7. Once all of your imports have completed you can click the **Clear Completed** button in order to clear the queue.
 