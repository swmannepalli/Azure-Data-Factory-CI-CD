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
+ Create Linked Services for following resources, these are the Dev resources that are deployed as part of Module 00 - Lab Environment Setup. <br />

	&nbsp; - **Azure KeyVault**: Select subscription where the dev resources are deployed. Select Dev Key Vault Name and leave Authentical Method to System Assigned Managed Identity. <br />

<img width="482" alt="image" src="https://user-images.githubusercontent.com/84516667/197681142-33966dd2-6bed-43d2-8293-f6947d3f5905.png">

&nbsp; - **Azure Data Lake Storage Gen2**: 


			
    

