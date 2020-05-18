Installation
------------
<h4>Is the MySQL extension supported in PHP, or just the MySQLi extension?</h4>

For security reasons DomainMOD only supports the MySQLi extension. If you're receiving messages that the MySQLi extension is unavailable in PHP you will need to install and enable it on your server before you can use DomainMOD.

!!! note
    As of v4.07, DomainMOD uses the PDO extension instead of the MySQLi extension.


<BR>Configuration
-----------------
<h4>Can I import my domains into DomainMOD using a CSV file?</h4>

Not currently, but this is something that we're investigating for the future. If your domain registrar has an API, and it's [supported by DomainMOD](domain-queue.md#supported-registrars), you can use the [Domain Queue](domain-queue.md) to automatically import your domains.

<h4>Does DomainMOD support multiple languages?</h4>

Currently only English is supported, but this is something that will be investigated for the future.


<h4>Which domain registrar APIs does DomainMOD currently support?</h4>

DomainMOD currently supports Above.com, DNSimple, DreamHost, Dynadot, eNom, Fabulous, Freenom (Reseller Accounts Only), Gandi, GoDaddy, Internet.bs, Name.com, NameBright, Namecheap, NameSilo, OpenSRS, and ResellerClub.


<BR>Usage
---------
<h4>How many domains can I manage with DomainMOD?</h4>

Theoretically there's no limit on the number of domains you can manage, it just depends on your server hardware and the settings chosen in DomainMOD. The default settings can handle thousands of domains, and over 10,000 depending on how much information you've chosen to display on the front page, but if things start slowing down you can enable **large mode** to speed things up. Large mode uses a different method for displaying the information on the main domain page, and although it doesn't offer as many of the advanced features as the default settings, it allows you to manage a lot more domains.


<h4>Can I use DomainMOD to sell domains?</h4>

The primary use for DomainMOD is to manage a large portfolio of domains, and it currently doesn't have any sales features, such as being able to host sales letter landing pages. This is something we're looking at implementing in a future version of DomainMOD.

If all you want to do is track the amount you sold a domain for, you can create a Custom Field, which will allow you to record the sales amount for your domains.


<h4>I don't need to keep track of the fees associated with my domains. Can I disable this feature?</h4>

There's currently no way to disable fees, as the system requires them in order to link the database tables, but if you don't care about keeping track of the fees you can just enter zeros for all of the costs.


<h4>I noticed you can set the registration, transfer, and renewal prices for domains via their domain registrars, but can you set a purchase price for a specific domain? For example, if I purchase a domain from a 3rd party marketplace can I record this information in DomainMOD?</h4>

Although this is not a standard field, you can use [Custom Fields](administration.md#custom-fields) to keep track of the purchase price of your domains.


<h4>Is it possible to display the custom fields I've created on the main domain page as a column?</h4>

This is something we're still investigating, as we realize how helpful this feature would be for some people, however if it happens it's probably going to be a while still. Although on the surface it seems like it may be pretty easy to implement, there's actually quite a bit to it and it's going to take quite a bit of work.

Also, since you can accomplish pretty much the same thing by exporting your domain list and sorting the exported data in something like excel (since it includes all of your custom fields), implementing this within the UI is not very high on the priority list.

!!! note
    As of v4.13, you can now display your Custom Fields on the main domain page.


<h4>Are the domain expiration dates updated automatically using the domain's WHOIS information?</h4> 

No, expiration dates currently need to be updated manually when the domains are renewed. Expiration dates can be updated one-by-one or by using the [Bulk Updater](bulk-updater.md).


<a name="registryapis"></a><h4>Do you plan to add API support for domain registries?</h4>

For API imports we've been trying to focus on actual registrars, since unlike registries they cover more than just one (or a few) domain extensions, and actual registrars are what most domainers use, which is who DomainMOD is primarily for. There are always exceptions to this of course, but in general this is the case.

Also, if we were to start adding API import support for registries this would open up a pretty big can of worms, since there are literally hundreds of registries that could be added. If we add one registrar we add support for all of the extensions that registrar has, whereas if we add support for a registry we only add support for a single extension (or in some cases a few extensions).

So although registry support may happen at *some* point, it's not currently very high on the priority list.


<h4>Is it possible to encrypt the data stored in DomainMOD?</h4>

It's not currently possible to encrypt the data in the database, however it's something we're hoping to implement in some way in the future. Based on our research it wouldn't be a small task to implement, and unfortunately, all things considered, it's just not one of the top priorities at the moment. Adding encryption would also create quite a few challenges with some features we have planned for the future.

For more information regarding the security of DomainMOD, please see [Security](getting-started.md#security) in the Getting Started section.
