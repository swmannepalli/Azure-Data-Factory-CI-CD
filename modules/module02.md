**Module 02 - Data Factory Development Workflow**
---------------------------------------------------------------------------------------------------------------------------------------------------------

[< Previous Module](module01.md) - [Home](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD) - [Next Module >](module03.md)

🤔 Prerequisites
---------------------------------------------------------------------------------------------------------------------------------------------------------

You need to complete [Module 00 - Lab Environment Setup](module00.md) and [Module 01 - Create a project in Azure DevOps](module01.md)

---------------------------------------------------------------------------------------------------------------------------------------------------------

** Setting up Code Repository**
---------------------------------------------------------------------------------------------------------------------------------------------------------

We can setup the code repository while creating the data factory by checking the enable Git box or after creation of Data Factory.
In this lab, we're setting up the repository after creation of Data Factory. Launch Data Factory Studio, go to Author. Select “Set up code repository” from the Data Factory drop-down list as shown below,

![image](https://user-images.githubusercontent.com/84516667/197676259-5c381c3d-fbe5-4040-ace2-d7fabb21dfa2.png)

**Configure a repository**
---------------------------------------------------------------------------------------------------------------------------------------------------------

+ Select Repository type as Azure DevOps Git and select your Azure Active Directory. Click on Continue.
+ Under Select repository, select your DevOps organization name from the drop down. Select Project and Repository name from the drop down.
+ We will create a new Collaboration branch by name "main"
+ Publish branch defaults to adf_publish.
+ Leave remaining settings to default and click on Apply
+ As per recommended guidlines, all developers should work in their own Working branch and not in main branch. So, in the next pop-up, click on Create new to create a Working branch. You can provide any name, for this lab let's use feature1 as the name.
---------------------------------------------------------------------------------------------------------------------------------------------------------

**Create Pipelines in Working Branch**
---------------------------------------------------------------------------------------------------------------------------------------------------------

+ For this lab, we will see how a copy activity with source as Azure Data Lake Storage Gen2 and Sink as Azure SQL Database is deployed to Production with minimal changes to connection strings/account keys. 
+ **Create Linked Services** for following resources, these are the Dev resources that are deployed as part of Module 00 - Lab Environment Setup. <br />

	&ensp; - **Azure KeyVault**: Select subscription where the dev resources are deployed. Select Dev Key Vault Name and leave Authentical Method to System Assigned Managed Identity. Refer [Screenshot](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD/blob/ce89dfd5e47197410d78d4ab2d1380b42781e857/Files/Screenshots/AzureKeyVault_LinkedService_Properties.jpg) 

	&ensp; - **Azure Data Lake Storage Gen2**: Select Authentication type as Account Key, Account selection method is Enter manually. Enter URL of the accountname (https://<youralias>devadls.dfs.core.windows.net) and select Azure Key Vault created above. Select the secret name ADLSAccountKey. Refer [Screenshot](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD/blob/ce89dfd5e47197410d78d4ab2d1380b42781e857/Files/Screenshots/ADLS_LinkedService_Properties.jpg)

	&ensp; - **Azure SQL Database**: Select Azure Key Vault, and select AKV linked service created above. Select AzureSQLCS as Secret name. Click Create. Refer [Screenshot](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD/blob/ce89dfd5e47197410d78d4ab2d1380b42781e857/Files/Screenshots/AzureSQL_LinkedService_Properties.jpg)
	
	
+ **Create Datasets**
