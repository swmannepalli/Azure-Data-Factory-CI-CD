**Module 00 - Lab Environment Setup**
------------------------------------------------------------------------------------------------------------------------------------------------------------------
 [Home](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD) -  [Next Module (Create project in Azure DevOps) >](module01.md)

**📢 Introduction**
------------------------------------------------------------------------------------------------------------------------------------------------------------------

In order to follow along with the ADF DevOps integration lab exercises, you need to provision a set of resources. One for Dev and one for Prod as the lab demonstrates deployment from Dev to Production. This module will help you to create following resources: <br />
 	
+ Dev and Prod Resource Groups
+ Dev and Prod ADLS Gen2
+ Dev and Prod Azure Data Factory
+ Dev and Prod Azure SQL Database
+ Dev and Prod Azure KeyVault

🤔 Prerequisites
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
1. An Azure account with an active subscription. Note: If you don't have access to an Azure subscription, you may be able to start with a free account. All below resources should be created in your own subscription.
2. You must have the necessary privileges within your Azure subscription to create resources, perform role assignments, register resource providers (if required), etc.
	
🧪 **Lab Dev Environment Setup**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

1. **Create Resource Group** - Reference Document [Create Resource Group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups) <br />

	* Create a Resource Group with the following naming convention (do not forget to use your alias):<br />
		 + {youralias}-dev-rg  <br />
	* Choose the region that is most appropriate to your current location.
	
2. **Resources Deployment:**  Make a note of SQL User ID and Password as these are needed in later steps.

	+ **Deploy ADLS, ADF and Azure SQL resources in Dev Resource Group** -  Right-click or Ctrl + click the button below to open the Azure Portal in a new window and deploy resources in Dev Resource group created above. <br />	
	
		[![Deploy Dev Resources to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FDev%2FMainARMTemplate.json)
		
	+ **Deploy Azure KeyVault**  - Right-click or Ctrl + click the button below to open the Azure Portal in a new window to deploy Azure KeyVault. <br />
	
		[![Deploy Dev KV to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FDev%2FAzurekeyvault.json)
		
	  **Parameter Values**  <br />
		- User ObjectId - Go to Azure-Data-Factory-CI-CD/TeamMembers-Object-IDs.md in this repo and get your respective Object ID value.
		- ADF ObjectId - Go to Dev ADF created above --> Managed Identities --> copy Object Id.
		- Azure Sqlsecret Value - Go to {youralias}-dev-sqldb --> Connection Strings --> Copy ADO.NET (SQL authentication). Make sure to replace the  password.
		- Adlssecret Value - {youralias}devadls --> Access Keys --> Click on Show for Key1 and copy    	

🧪 **Lab Prod Environment Setup**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
1. **Create Resource Group** - Reference Document [Create Resource Group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups) <br />

	* Create a Resource Group with the following naming convention (do not forget to use your alias):<br />
		 + {youralias}-prod-rg  <br />
	* Choose the region that is most appropriate to your current location. <br />
2. **Resources Deployment:**  Make a note of SQL User ID and Password as these are needed in later steps.

	 + **Deploy ADLS, ADF and Azure SQL resources in Prod Resource Group** - Right-click or Ctrl + click the button below to open the Azure Portal in a new window and deploy resources in Prod Resource group created above. <br />	

		[![Deploy Prod Resources to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FProd%2FMainARMTemplate.json)
		
	+ **Deploy Azure KeyVault** - Right-click or Ctrl + click the button below to open the Azure Portal in a new window to deploy Azure KeyVault. <br />
	
		[![Deploy Prod KV to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fswmannepalli%2FAzure-Data-Factory-CI-CD%2Fmain%2FARMTemplates%2FProd%2FAzurekeyvault.json)
	
	  **Parameter Values**  <br />
		- User ObjectId - Go to Azure-Data-Factory-CI-CD/TeamMembers-Object-IDs.md in this repo and get your respective Object ID value.
		- ADF ObjectId - Go to Prod ADF created above --> Managed Identities --> copy Object Id.
		- Azure Sqlsecret Value - Go to {youralias}-prod-sqldb --> Connection Strings --> Copy ADO.NET (SQL authentication). Make sure to replace the  password.
		-  Adlssecret Value - {youralias}prodadls --> Access Keys --> Click on Show for Key1 and copy
	
		
	
If you do not have the required permissions to fulfil these pre-requisites or need assistance, please e-mail swmannepalli@microsoft.com to ensure a successful lab experience.

 [Continue >](module01.md)
