**Module 02 - Data Factory Development Workflow**
---------------------------------------------------------------------------------------------------------------------------------------------------------

[< Previous Module](module01.md) - [Home](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD) - [Next Module >](module03.md)

🤔 Prerequisites
---------------------------------------------------------------------------------------------------------------------------------------------------------

You need to complete [Module 00 - Lab Environment Setup](module00.md) and [Module 01 - Create a project in Azure DevOps](module01.md)

---------------------------------------------------------------------------------------------------------------------------------------------------------

**Development Workflow**
-------------------------------------------------------------------------------------------------------------------------------------------------------

<img width="2376" alt="image" src="https://user-images.githubusercontent.com/84516667/198290530-226184ca-5e08-457b-ab6e-9e85b1d6eb01.png">


**Setting up Code Repository in Dev Data Factory**
---------------------------------------------------------------------------------------------------------------------------------------------------------

We can setup the code repository while creating the data factory by checking the enable Git box or after creation of Data Factory.
In this lab, we're setting up the repository after creation of Data Factory. Launch Dev Data Factory Studio, go to Author. Select “Set up code repository” from the Data Factory drop-down list as shown below,

![image](https://user-images.githubusercontent.com/84516667/197676259-5c381c3d-fbe5-4040-ace2-d7fabb21dfa2.png)


**Configure a repository**
---------------------------------------------------------------------------------------------------------------------------------------------------------

+ Select Repository type as Azure DevOps Git and select your Azure Active Directory. Click on Continue.
+ Under Select repository, select your DevOps organization name from the drop down. Select Project and Repository name from the drop down.
+ Create a new Collaboration branch by name "master"
+ Publish branch defaults to adf_publish.
+ Leave remaining settings to default and click on Apply
+ As per recommended guidlines, all developers should work in their own feature branch and not in master branch. So, in the next pop-up, click on Create new to create a feature branch. The usual naming convention is feature_XY where XY can be the work item number from Azure DevOps board on which you are working. For this lab let's use feature1 as the name. 
+ On creating of feature1 branch, it will automatically be selected which means it is currently being checked out in the repository and any changes will be done now will be committed in that branch. Each time you click Save, it will create a corresponding commit in the selected branch.
---------------------------------------------------------------------------------------------------------------------------------------------------------

**Create Pipelines in Feature Branch**
---------------------------------------------------------------------------------------------------------------------------------------------------------
**Note**: Make sure the branch is pointing to feature branch before you create below artifacts.
<img width="488" alt="image" src="https://user-images.githubusercontent.com/84516667/197802694-9bc0d1b1-3c54-4207-a0dd-44624f1cf31e.png">

+ In this lab, a copy activity with source as Azure Data Lake Storage Gen2 and Sink as Azure SQL Database is deployed from Dev Data Factory to Production with minimal changes to connection strings/account keys. 
+ **Create Linked Services** for following resources, these are the Dev resources that are deployed as part of Module 00 - Lab Environment Setup. <br />

	&ensp; - **Azure KeyVault**: Select subscription where the dev resources are deployed. Select Dev Key Vault Name and leave Authentical Method to System Assigned Managed Identity. Refer [Screenshot](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD/blob/ce89dfd5e47197410d78d4ab2d1380b42781e857/Files/Screenshots/AzureKeyVault_LinkedService_Properties.jpg) 

	&ensp; - **Azure Data Lake Storage Gen2**: Select Authentication type as "Account Key", Account selection method as "Enter manually". Enter URL of the accountname by replacing youralias with actual alias value (https://youraliasdevadls.dfs.core.windows.net) and select Azure Key Vault created above. Select the secret name ADLSAccountKey. Refer [Screenshot](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD/blob/ce89dfd5e47197410d78d4ab2d1380b42781e857/Files/Screenshots/ADLS_LinkedService_Properties.jpg)

	&ensp; - **Azure SQL Database**: Select Azure Key Vault, and select AKV linked service created above. Select AzureSQLCS as Secret name. Click Create. Refer [Screenshot](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD/blob/ce89dfd5e47197410d78d4ab2d1380b42781e857/Files/Screenshots/AzureSQL_LinkedService_Properties.jpg)
	
	
+ **Create Datasets** for the linked services created above. <br /> Note: We will not be copying any files as part of this lab as this is intended to show how pipeline deployments happen by leveraging KeyVault Secret Names. So, for ADLS Gen2 Dataset, randomly select a file format and root folder (By clicking browse button next to File path). 
	
	&ensp; - **Azure Data Lake Storage Gen2**: Select the linked service created above, select any file format and click continue. Select browse button to select root folder and click on OK. For File name in File path, provide * and Click on save all. <br />
	&ensp; - **Azure SQL Database**: Select linked service and click on OK. In the next window, under connection, click on Edit for Table and provide dbo for schema and any table name. Click on Save all <br />

<img width="575" alt="image" src="https://user-images.githubusercontent.com/84516667/198135416-ea64fdf2-c5f7-4ebc-808d-7666ad42d033.png">

	
+ **Create Copy Activity** - For Source, select ADLS Gen2 Dataset. For Sink, select Azure SQL Database Dataset. Click on Save all to save all changes.
---------------------------------------------------------------------------------------------------------------------------------------------------------
**Publishing Changes (Automated)**
---------------------------------------------------------------------------------------------------------------------------------------------------------

+ To acheive automatic publishing of chnages to dev environment, we need to create a build pipeline using YAML that will package the artifacts for continuous integration whenever the code changes in master branch.

To complete the development lifecycle, <br />

+ Developers should perform unit test cases in their feature branch to make sure there are no errors and the code is matching to their requirements. In this case, click on Validate all to check there are no errors in the pipeline created above.  <br />
+ To merge changes back to Collaboration branch, expand the feature1 branch on the left top, and click on Create Pull Request. This will take you to the Azure DevOps page.  <br />
+ Provide Title and add reviewers if required. This is recommended approach so there are some other users who can validate your branch work to prevent any errors in main/collaboration branch. For this lab, you can skip it and click on Create and Complete. A pop up window appears, and it is best approach to delete feature1 branch after merging which helps in keeping the commit history and repo clean. Click on Complete Merge.  <br />
	
Now, Azure DevOps repo will contain the Data Factory Artifacts. <br /> 
	
<img width="1211" alt="image" src="https://user-images.githubusercontent.com/84516667/197806842-9274947a-fe6d-402c-bad1-e5d1b94528b1.png">

+ You'll see only main branch in the repo and no publish branch yet. At this point, code is merged to main branch but not yet published. Now that all the code is in main branch, perform integration test cases to make sure end to end code is working without any errors. 
+ Go back to the Data Factory Studio, go back to main branch and click on Publish. At this point, changes are deployed to Data Factory, publishes to collaboration branch and generates ARM Template (this is what we use to deploy code to other environments). Now, if you go to Azure DevOps and check branches, adf_publish branch is created.

[Continue >](module03.md)
