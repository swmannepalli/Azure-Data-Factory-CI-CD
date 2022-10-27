**Module 03 - Data Factory Development Workflow**
---------------------------------------------------------------------------------------------------------------------------------------------------------

[< Previous Module](module02.md) - [Home](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD) - [Next Module >](module04.md)

🤔 Prerequisites
---------------------------------------------------------------------------------------------------------------------------------------------------------

You need to complete [Module 00 - Lab Environment Setup](module00.md) and [Module 01 - Create a project in Azure DevOps](module01.md)

---------------------------------------------------------------------------------------------------------------------------------------------------------

**Development Workflow**
-------------------------------------------------------------------------------------------------------------------------------------------------------

<img width="2376" alt="image" src="https://user-images.githubusercontent.com/84516667/198290530-226184ca-5e08-457b-ab6e-9e85b1d6eb01.png">


**Publishing Changes (Automated)**
---------------------------------------------------------------------------------------------------------------------------------------------------------

+ To acheive automatic publishing of chnages to dev environment, we need to create a build pipeline using YAML that will package the artifacts for continuous integration whenever the code changes in master branch.

Login to https://dev.azure.com to open Azure DevOps. Navigate to the project where you have hosted the source code repository of Azure Data Factory V2 objects. To create a new pipeline under a project, Select Pipelines -> Create Pipeline. 

<img width="1467" alt="image" src="https://user-images.githubusercontent.com/84516667/198354721-ad29aedd-9f7e-4a9c-a608-8a1a1da9e52d.png">

Select Azure Repos Git as our code resides in Azure Repos and select the repo where the ADF v2 objects are hosted. Select Starter pipeline.

<img width="490" alt="image" src="https://user-images.githubusercontent.com/84516667/198354977-1c9eef72-dcbf-4435-bbd2-ec40ac7606c1.png"> <img width="500" alt="image" src="https://user-images.githubusercontent.com/84516667/198355031-d9443573-53d4-4f1e-be16-48eb3f9f5724.png">

Copy the [this](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD/blob/d41c0db778ca6f49e7354f26039f625d09004b59/Files/azure-pipelines.yml) (Right click to open in new window) code and paste in the azure-pipelines.yml file and click Save. This will prompt you to commit the file to the repository. Select “commit directly to the master branch” option to commit this file. The commit message is already populated with a predefined message. Alternatively, you can write a custom commit message.


To complete the development lifecycle, <br />

+ Developers should perform unit test cases in their feature branch to make sure there are no errors and the code is matching to their requirements. In this case, click on Validate all to check there are no errors in the pipeline created above.  <br />
+ To merge changes back to Collaboration branch, expand the feature1 branch on the left top, and click on Create Pull Request. This will take you to the Azure DevOps page.  <br />
+ Provide Title and add reviewers if required. This is recommended approach so there are some other users who can validate your branch work to prevent any errors in main/collaboration branch. For this lab, you can skip it and click on Create and Complete. A pop up window appears, and it is best approach to delete feature1 branch after merging which helps in keeping the commit history and repo clean. Click on Complete Merge.  <br />
	
Now, Azure DevOps repo will contain the Data Factory Artifacts. <br /> 
	
<img width="1211" alt="image" src="https://user-images.githubusercontent.com/84516667/197806842-9274947a-fe6d-402c-bad1-e5d1b94528b1.png">

+ You'll see only main branch in the repo and no publish branch yet. At this point, code is merged to main branch but not yet published. Now that all the code is in main branch, perform integration test cases to make sure end to end code is working without any errors. 
+ Go back to the Data Factory Studio, go back to main branch and click on Publish. At this point, changes are deployed to Data Factory, publishes to collaboration branch and generates ARM Template (this is what we use to deploy code to other environments). Now, if you go to Azure DevOps and check branches, adf_publish branch is created.

[Continue >](module04.md)
