{!_csv-importer-shared.md!}

You can import as little or as much domain information as you want. Technically you can fill in nothing but a list of domains, and it will import just fine, but DomainMOD will need to create a bunch of generic Assets for you. It's ok though, even if you go this route it's pretty easy to update the information that DomainMOD creates for you.

Regardless of how well testing has gone so far, we always recommended that you perform a full backup of your existing DomainMOD database before attempting a CSV Import, just in case something goes wrong and you need to recover.

!!! note
    Before you can use the CSV Importer you must update the permissions on the /var/www/html/domainmod/temp folder ("***chmod 777 /var/www/html/domainmod/temp***"). If you're unsure how to do this your web hosting provider should be able to assist you.

# Usage
Once logged into DomainMOD, click **Domains** in the main menu and then click on the **CSV Importer** button. You will then be walked through how to import your domain data using our CSV Import Template.

# CSV Import Template
[Click here](import-template-sample.csv) to download the sample CSV Import Template file.

!!! danger "Warning"
    The columns in the CSV Import Template must remain as-is. If there are an incorrect number of columns, or the columns are not in the correct order, the CSV import will fail.

# Template Columns
Below is a list of all the columns that appear in the CSV Import Template file, along with a description of what the column is for. The only **required** column is the **domain** column, but the more information you enter into the CSV file, the more complete your DomainMOD installation will be.

### Domain Fields
**domain (*required*)**  
The domain name.  

**expiry_date**  
The domain's expiry date.  
*Format: YYYY-MM-DD*

**function**  
The function/purpose of the domain.  

**auto_renewal**  
Is auto renew enabled?  
*Options (Numeric): 0, 1*  
*Options (Text): NO, YES (text options are case-insensitive)*

**privacy**  
Is WHOIS privacy enabled?  
*Options (Numeric): 0, 1*  
*Options (Text): NO, YES (text options are case-insensitive)*

**status**  
The domain's status.  
*Options (Numeric): 0, 1, 2, 3, 4, 5, 10*  
*Options (Text): EXPIRED, ACTIVE, PENDING (TRANSFER), PENDING TRANSFER, PENDING (RENEWAL), PENDING RENEWAL, PENDING (OTHER), PENDING OTHER, PENDING (REGISTRATION),  PENDING REGISTRATION, SOLD  (text options are case-insensitive)*

**registration_fee**  
The cost of the domain's initial registration.  

**renewal_fee**  
The cost of the yearly domain renewal.

**transfer_fee**  
The cost that the domain's current registrar charges to transfer this TLD in.

**privacy_fee**  
The cost of WHOIS privacy for the domain.  

**miscellaneous_fee**  
Any additional fees related to the domain.  

**fee_currency**  
The currency for the domain's fees.  
*Example: USD*

**domain_ip_address_name**  
The name you want to assign to the domain's IP address. 

**domain_ip_address**  
The domain's IP address.

**domain_ip_address_rdns**  
The reverse DNS of the domain's IP address.

**domain_ip_address_notes**  
Any notes you have for the domain's IP address. 

**domain_notes**  
Any notes you have for the domain.

### Domain Category Fields
**category**  
The name of the category that the domain belongs to.

**category_stakeholder**  
The individual or company responsible for the specific domain category.  

**category_notes**  
Any notes you have for the domain's category.  

### Web Hosting Provider Fields
**hosting_provider**  
The name of this domain's web hosting provider.

**hosting_provider_url**  
The URL of the domain's web hosting provider.  

**hosting_provider_notes**  
Any notes you have for this domain's web hosting provider.  

### Domain Registrar Fields
**registrar_name**  
The domain registrar's name.  

**registrar_url**  
The domain registrar's URL.

**registrar_notes**  
Any notes you have for this domain's domain registrar.  

### Domain Registrar Account Fields
**registrar_account_owner**  
The individual or company that technically owns the domain registrar account.   

**registrar_account_owner_notes**  
Any notes you have about the domain registrar account owner.  

**registrar_account_email_address**  
The email address for the domain registrar account.  

**registrar_account_username**  
The username for the domain registrar account.

**registrar_account_password**  
The password for the domain registrar account.  

**registrar_account_account_id**  
The account ID for the domain registrar account.  

**registrar_account_reseller**  
The reseller status for the domain registrar account.    
*Options (Numeric): 0, 1*  
*Options (Text): NO, YES (text options are case-insensitive)*

**registrar_account_reseller_id**  
The reseller ID for the domain registrar account.  

**registrar_account_notes**  
Any notes you have for the domain registrar account.  

**api_app_name**  
Certain domain registrars require you to supply an API app name in order to use their API.

**api_key**  
Most domain registrars require you to supply an API key in order to use their API.

**api_secret**  
Most domain registrars require you to supply an API secret in order to use their API.  

**api_ip_address_name**  
Some registrars require you to restrict your API access to specific IP addresses. This is the name you want to assign to that IP address. 

**api_ip_address**  
The API IP address.

**api_ip_address_rdns**  
The reverse DNS of the API IP address.

**api_ip_address_notes**  
Any notes you have for the API IP address.

### DNS Fields
**dns_profile_name**  
The name you want to assign to the grouping of DNS servers used by this domain.

**dns_server_1 - dns_server_10**  
The (2-10) DNS servers used by this domain.

**dns_ip_1 - dns_ip_10**  
The (2-10) IP addresses used by this domain's DNS servers.  

**dns_notes**  
Any notes you have for the set of DNS servers.