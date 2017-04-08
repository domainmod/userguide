DomainMOD gives you a few options for adding your domains, so you should read through the below sections to determine which will work best for you.

**NOTE:** Before adding your domains to DomainMOD you must first create some Assets. If you've just finished installing you should visit the [First Run](first-run.md) section, which will walk you through creating the assets that are required to start using DomainMOD.

Domain Queue
---------------
The easiest option for adding domains is to use the Domain Queue, which allows you to supply a list of domains and let DomainMOD take care of the rest (and in some cases you don't even need to supply the list of domains, it will be automatically retrieved from your registrar account).

This option uses your domain registrar's API to retrieve information required to add domains, so unfortunately it only works if your registrar has an API and support for it has been built into DomainMOD. Before using this option make sure your API credentials have been saved with your registrar account.

Currently Supported Registrars: DNSimple, Dynadot, eNom, Fabulous, GoDaddy, Internet.bs, Name.com, NameBright, Namecheap, NameSilo, OpenSRS, ResellerClub

**NOTE:** In order to use the Domain Queue you must first [setup the cron job](getting-started.md#cron-job) that comes with DomainMOD.

[Add domains using the Domain Queue &raquo;](domain-queue.md)

Bulk Updater
--------------  
The Bulk Updater also allows you to supply a list of domains to be added, however you need to manually choose the options for the domains you're adding, and all of the domains will have the same settings. The Bulk Updater generally works best if you're adding a list of newly registered domains, since they will have the same expiry date and will generally have the same settings.

[Add domains using the Bulk Updater &raquo;](bulk-updater.md) 

Manually
---------
Domains can also be added one-by-one, which allows you to choose custom settings for each domain.

**Adding A Domain Manually**

1. Click on **Domains** on the main menu.

2. Click on the **Add Domain** button on the Domains page.

3. Enter the Domain that you want to add.

4. Fill in all of the relevant details for the domain, such as the expiry date, registrar account, DNS profile, and so on. 

5. Click the **Add Domain** button.

That's it, your domain has been added to DomainMOD!

**NOTE:** If this is the first time you've added a domain with this TLD from this registrar, you will need to enter the fees associated with this registrar/TLD combination. If this is the case, after adding the domain you will be presented with a notice that will walk you through how to add the new fee.
