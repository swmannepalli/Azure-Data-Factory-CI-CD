**Azure Data Factory CI/CD Lab prerequisites**

To have a successful experience for the Azure Data Factory CI/CD lab, please ensure that you meet the following pre-requisites:

one for Dev and one for Prod as the lab demonstrates deployment from Dev to Production.  

1. **Azure subscription** - Use your own internal subscription to create all resources
2. **Create Resource Groups** - Reference Document [Create Resource Group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups) <br />

	* Create two Resource Groups (one for Dev and one for Prod) with the following naming convention (do not forget to use your alias):<br />
		 + {youralias}-dev-rg  <br />
		 + {youralias}-prod-rg <br />
	* Choose the region that is most appropriate to your current location.
3. **Dev Resources Deployment:**  Make a note of SQL User ID and Password as these are needed in later steps.

	+ **Deploy ADLS, ADF and Azure SQL resources in Dev Resource Group** - Click Deploy to Azure button to deploy resources in Dev Resource group created above. <br /> <br />
	Right-click or Ctrl + click the button below to open the Azure Portal in a new window. <br />
	
		[![Deploy Dev Resources to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FDev%2FMainARMTemplate.json)
		
	+ **Deploy Azure KeyVault** - <br />
		**Parameter Values** - <br />
		- User ObjectId - Go to Azure-Data-Factory-CI-CD/TeamMembers-Object-IDs.md in this repo and get your respective Object ID value.
		- ADF ObjectId - Go to Dev ADF created above --> Managed Identities --> copy Object Id.
		- Azure Sqlsecret Value - Go to {youralias}-dev-sqldb --> Connection Strings --> Copy ADO.NET (SQL authentication). Make sure to replace the  password.
		- Adlssecret Value - {youralias}devadls --> Access Keys --> Click on Show for Key1 and copy
<br /> <br />
	
		[![Deploy Dev KV to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FDev%2FAzurekeyvault.json)

4. **Prod Resources Deployment:**  Make a note of SQL User ID and Password as these are needed in later steps.

	 + **Deploy ADLS, ADF and Azure SQL resources in Prod Resource Group** - Click Deploy to Azure button to deploy resources in Prod Resource group created above. 

		[![Deploy Prod Resources to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FProd%2FMainARMTemplate.json)
		
	+ **Deploy Azure KeyVault** - <br />
		**Parameter Values** - <br />
		- User ObjectId - Go to Azure-Data-Factory-CI-CD/TeamMembers-Object-IDs.md in this repo and get your respective Object ID value.
		- ADF ObjectId - Go to Prod ADF created above --> Managed Identities --> copy Object Id.
		- Azure Sqlsecret Value - Go to {youralias}-prod-sqldb --> Connection Strings --> Copy ADO.NET (SQL authentication). Make sure to replace the  password.
		-  Adlssecret Value - {youralias}prodadls --> Access Keys --> Click on Show for Key1 and copy
	
		[![Deploy Prod KV to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FProd%2FAzurekeyvault.json)
	
If you do not have the required permissions to fulfil these pre-requisites or need assistance, please e-mail swmannepalli@microsoft.com to ensure a successful lab experience.
