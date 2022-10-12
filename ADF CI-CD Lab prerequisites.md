
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
	
5. **Create Azure Key Vaults** -  Reference Link [Create Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/quick-create-portal) <br />

	* Create two Azure Key Vaults with the following naming convention:<br />
		+ {youralias}-dev-kv --> This is created in dev resource group <br /> 
		+ {youralias}-prod-kv --> This is created in prod resource group <br /> 
	* Choose the region that is most appropriate to your current location
	* Pricing tier - Standard
	* Default values for rest of the settings <br />

If you do not have the required permissions to fulfil these pre-requisites or need assistance, please e-mail swmannepalli@microsoft.com to ensure a successful lab experience.
