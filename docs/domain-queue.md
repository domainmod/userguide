{!domain-queue-shared.md!}

Supported Registrars
--------------------
The following registrars are currently supported by the Domain Queue:

Above.com, DNSimple, DreamHost, Dynadot, eNom, Fabulous, Freenom (Reseller Accounts Only), GoDaddy, Internet.bs, Name.com, NameBright, Namecheap, NameSilo, OpenSRS, ResellerClub

Usage
-----

!!! warning "Requirement"
    In order to use the Domain Queue you must first setup the [cron job](getting-started.md#cron-job) that comes with DomainMOD.

1. Click on **Domains** on the main menu.

2. Click the **Add Domains To Queue** button on the Domains page.

3. On the dropdown list, choose the registrar account that you would like to import using the Domain Queue.

4. If requested, paste in a list of the domains you want to add to the Domain Queue. This is not always required, as some domain registrars will retrieve the list of domains from your account automatically.

5. Click the **Add Domains** button.

6. You will now be taken to the Domain Queue page, where you can see the status of your domain imports. You can also access the Domain Queue by clicking on **Queue** on the main menu (this menu option is only available when you have domains being processed in the queue).

7. Once all of your imports have completed you can click the **Clear Completed** button in order to clear the queue.

<a name="apinotes"></a>API Notes
-----
This section contains various notes and things to watch out for when using the domain registrar APIs.

<h4>DreamHost</h4>

DreamHost does not currently allow the WHOIS privacy status of a domain to be retrieved via their API, so all domains added to the Domain Queue from a DreamHost account will have their WHOIS privacy status set to No by default.

<h4>Freenom</h4>

Freenom currently only gives API access to reseller accounts.

<h4>GoDaddy</h4>

When retrieving your list of domains from GoDaddy, the current limit is 1,000 domains. If you have more than this you should export the full list of domains from GoDaddy and paste it into the **Domains to add** field when adding domains via the Domain Queue.

<h4>NameSilo</h4>

NameSilo's domains have 6 possible statuses: Active, Expired (grace period), Expired (restore period), Expired (pending delete), Inactive, and Pending Outbound Transfer

When retrieving your list of domains via the API, **Inactive** domains are not returned.

When retrieving the details of a specific domain via the API, **Inactive** and **Expired (pending delete)** domains will not return any data.

<h4>ResellerClub</h4>

ResellerClub does not allow users to retrieve a list of their domains via the API, nor do they return the Auto Renewal status when retrieving the details of a domain. All domains imported via the API will have their Auto Renewal status set to No by default.