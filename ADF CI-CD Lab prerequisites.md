
**Azure Data Factory CI/CD Lab prerequisites**

To have a successful experience for the Azure Data Factory CI/CD lab, please ensure that you meet the following pre-requisites:

We create each service twice listed below, one for Dev and one for Prod as the lab demonstrates deployment from Dev to Production.  

1. **Azure subscription** - Use your own internal subscription to create all resources
2. **Create Resource Groups** - Reference Link [Create Resource Group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups) <br />

	* Create two Resource Groups with the following naming convention (do not forget to use your alias):<br />
		 + {youralias}-dev-rg  <br />
		 + {youralias}-prod-rg <br />
	* Choose the region that is most appropriate to your current location.
	
3. **Create Azure Data Lake Storage Gen2 storage accounts** -  Reference Link [Create ADLS Gen2 Account](https://learn.microsoft.com/en-us/azure/storage/blobs/create-data-lake-storage-account)  <br />

 	* Create two storage accounts with the following naming convention:<br />
		+ {youralias}devadls --> This is created in dev resource group <br /> 
		+ {youralias}prodadls --> This is created in prod resource group <br /> 
	* Choose the region that is most appropriate to your current location.
	* Performance - Standard
	* Redundancy - LRS
	* Under Advanced - Leave everything to default and check Enable hierarchical namespace
	* Default values for rest of the settings <br />

4. **Create Azure SQL Databases** -  Reference Link [Create Azure SQL Database](https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal) <br />

	* Create two Azure SQL Databases with the following naming convention:<br />
		+ {youralias}-dev-db --> This is created in dev resource group <br /> 
		+ {youralias}-prod-db --> This is created in prod resource group <br /> 
	* Choose to create new server with the following name(s):<br />
		+ {youralias}-dev-server
		+ {youralias}-prod-server
	* Default values for rest of the settings <br />
	
5. **Create Azure Key Vaults** -  Credentials for ADLS and Azure SQL are stored here. Reference Link [Create Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/quick-create-portal) <br />

	* Create two Azure Key Vaults with the following naming convention:<br />
		+ {youralias}-dev-kv --> This is created in dev resource group <br /> 
		+ {youralias}-prod-kv --> This is created in prod resource group <br /> 
	* Choose the region that is most appropriate to your current location
	* Pricing tier - Standard
	* Default values for rest of the settings <br />
6. **Create Azure Data Factories** - Reference Link [Create Azure Data Factory](https://learn.microsoft.com/en-us/azure/data-factory/quickstart-create-data-factory)<br />
	* Create two Azure Data Factories with the following naming convention:<br />
		+ {youralias}-dev-df --> This is created in dev resource group <br /> 
		+ {youralias}-prod-df --> This is created in prod resource group <br /> 
	* Choose the region that is most appropriate to your current location
	* Git Configuration - Check Configure Git later
	* Default values for rest of the settings <br />

7. **Create Secrets in Azure Key Vaults** - Here, we will create two secrets, one to store ADLS credential and one to store Azure SQL DB connection string.
	
	* **Dev Environment** - <br />
		 **ADLS Secret**
		+ To get connection string for storage account - Go to dev storage account created above, select Access Keys under Security + networking, click on show next to Connection string and copy the value.
		+ Go to dev azure key vault created above and select secrets under Objects. Click on Generate/Import
		+ Name - adlscredential
		+ Secret Value - Paste the connection string value copied above and click on create. <br />
	
		**Azure SQL DB Secret**
		+ To get connection string for SQL DB - Go to dev SQL DB created above, select Connection strings under Settings and copy ADO.NET (Active Directory integrated authentication) value. Replace {your_username} with your user ID
		+ Go to dev azure key vault created above and select secrets under Objects. Click on Generate/Import
		+ Name - sqlconnectionstring
		+ Secret Value - Paste the connection string value copied above and click on create.

	* **Prod Environment** - <br />
		 **ADLS Secret**
		+ To get connection string for storage account - Go to prod storage account created above, select Access Keys under Security + networking, click on show next to Connection string and copy the value.
		+ Go to prod azure key vault created above and select secrets under Objects. Click on Generate/Import
		+ Name - adlscredential
		+ Secret Value - Paste the connection string value copied above and click on create.<br />
		
		**Azure SQL DB Secret**
		+ To get connection string for SQL DB - Go to prod SQL DB created above, select Connection strings under Settings and copy ADO.NET (Active Directory integrated authentication) value. Replace {your_username} with your user ID
		+ Go to prod azure key vault created above and select secrets under Objects. Click on Generate/Import
		+ Name - sqlconnectionstring
		+ Secret Value - Paste the connection string value copied above and click on create. <br />
		
ADF should have access to Azure Key Vault to retrieve the secret value - Go to Access policies in Dev Key Vault and select create. Select All under Key and secret permissions and click on Next. Search for Dev ADF name and select it. Click Next and create. <br />

+ Repeat the same process to provide Prod ADF access to Prod Key Valut.<br />
	
If you do not have the required permissions to fulfil these pre-requisites or need assistance, please e-mail swmannepalli@microsoft.com to ensure a successful lab experience.
