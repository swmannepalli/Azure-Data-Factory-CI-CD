
**Azure Data Factory CI/CD Lab prerequisites**

To have a successful experience for the Azure Data Factory CI/CD lab, please ensure that you meet the following pre-requisites:

We create each service twice listed below, one for Dev and one for Prod as the lab demonstrates deployment from Dev to Production. Please 

1. **Azure subscription** - Use your own internal subscription to create all resources
2. **Create Resource Groups** - Reference Link [Create Resource Group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups)  <br />
	
	a. {youralias}-dev-rg  <br />
	b. {youralias}-prod-rg
	
**NOTE:** All the below resources should be created in the resource groups created above.

3. **Create Azure Data Lake Storage Gen2 storage account**: Reference Link [Create ADLS Gen2 Account](https://learn.microsoft.com/en-us/azure/storage/blobs/create-data-lake-storage-account)  <br />
	a. {youralias}-dev-adls  <br />
	b. {youralias}-prod-rg

4. Azure SQL Database: If you don't have a SQL DB account, see the instructions in Create a SQL DB.

S3 Browser: Download the S3 browser here.

If you do not have the required permissions to fulfil these pre-requisites, please e-mail swmannepalli@microsoft.com to ensure a successful lab experience.
