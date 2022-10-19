**Azure Data Factory CI/CD Lab prerequisites**

To have a successful experience for the Azure Data Factory CI/CD lab, please ensure that you meet the following pre-requisites:

one for Dev and one for Prod as the lab demonstrates deployment from Dev to Production.  

1. **Azure subscription** - Use your own internal subscription to create all resources
2. **Create Resource Groups** - Reference Document [Create Resource Group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups) <br />

	* Create two Resource Groups (one for Dev and one for Prod) with the following naming convention (do not forget to use your alias):<br />
		 + {youralias}-dev-rg  <br />
		 + {youralias}-prod-rg <br />
	* Choose the region that is most appropriate to your current location.
3. **Resources Deployment:** Go to Azure-Data-Factory-CI-CD/TeamMembers-Object-IDs.md in this repo and get your respective Object ID value. Use this value for userObjectId parameter.To get ADF Object ID, . Make a note of SQL User ID and Password as these are needed in later steps.

	+ **Deploy resources in Dev Resource Group** - Click Deploy to Azure button to deploy resources in Dev Resource group created above. 

		[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FDev%2FMainARMTemplate.json)

	 + **Deploy resources in Prod Resource Group** - Click Deploy to Azure button to deploy resources in Prod Resource group created above. 

		[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FProd%2FMainARMTemplate.json)

5. **Update Secrets in Azure Key Vaults** - As part of deployment, two secrets are cretaed in Dev and Prod Key Vaults - **ADLSAccountKey and AzureSQLCS**.One to store ADLS Account Key and one to store Azure SQL DB connection string. You need to provide your credentials for these secrets in both environments.
	
	 **ADLS Secret** - <br /> 
		a. To get account key for storage account - Go to dev storage account created above, select Access Keys under Security + networking, click on show next to Key and copy the value.
		b. Go to dev azure key vault created above and select secrets under Objects. 
		c. Click on ADLSAccountKey and select New Version. Paste the account key copied above in secret value and click on create. <br />
	**Note:** Repeat steps  a-c for Prod environment.
	
	**Azure SQL DB Secret**
		a. To get connection string for SQL DB - Go to dev SQL DB created above, select Connection strings under Settings and copy ADO.NET (SQL authentication) value. Replace {your_username} and password with vaules you provided during resource deployment.
		b. Go to dev azure key vault created above and select secrets under Objects. 
		c. Click on AzureSQLCS and select New Version. Paste the connection string copied above in secret value and click on create.<br />
	**Note:** Repeat steps  a-c for Prod environment.
		
ADF should have access to Azure Key Vault to retrieve the secret value - Go to Access policies in Dev Key Vault and select create. Select All under Key and secret permissions and click on Next. Search for Dev ADF name and select it. Click Next and create. <br />

+ Repeat the same process to provide Prod ADF access to Prod Key Vault.<br />
	
If you do not have the required permissions to fulfil these pre-requisites or need assistance, please e-mail swmannepalli@microsoft.com or paras.parekh@microsoft.com  to ensure a successful lab experience.
