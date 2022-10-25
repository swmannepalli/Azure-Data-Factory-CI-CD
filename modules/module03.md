**Module 03 - Release Lifecycle**
---------------------------------------------------------------------------------------------------------------------------------------------------------

[< Previous Module](module02.md) - [Home](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD) - [Next Module >](module04.md)

🤔 Prerequisites
---------------------------------------------------------------------------------------------------------------------------------------------------------

You need to complete [Module 00 - Lab Environment Setup](module00.md), [Module 01 - Create a project in Azure DevOps](module01.md) and [Module 02 - Data Factory Development Workflow](module02.md)

---------------------------------------------------------------------------------------------------------------------------------------------------------

**Creating Release Pipeline**
---------------------------------------------------------------------------------------------------------------------------------------------------------

Now that we've completed development lifecycle where publish branch has all the artifacts, we need to create release pipeline to deploy chnages to Prod environment.

+ Go to Azure DevOps project --> Pipelines --> Releases. Click on New pipeline
+ Let's start with Empty job --> Under Select a template, click on Empty job. Provide Stage name (this is environment name), in this lab it is going to be Prod. Click on Save and Ok.
<img width="845" alt="image" src="https://user-images.githubusercontent.com/84516667/197841827-e1efabef-a750-415d-bb9a-332450313b5a.png">

+ Click on Add an artifact, this we where we provide details about our dev environment artifacts. For Source type, select Azure Repos Git and select Project, repository. Select Default branch as adf_publish which is the branch to checkout. You can have separate branch created for this as well. Click on Add.
+ Now, we need to add a task to provide destination environment details i.e., Prod Data Factory environment. Click on the 1 job, 0 task under Prod Stage, click on '+' next to Agent job and search for Arm Template deployment and click on add. Select the job to fill out the configurations. 
+ For Azure Resource Manager Connection, select your subscription where Prod Data Factory is deployed and click on Authorize.
+ Once the authoriztion is complete, select the Subscription, Resource group and Location of Prod Data Factory.
+ For Template, browse and select ARMTemplateForFactory file.
+ For Template parameters, browse and select ARMTemplateParametersForFactory file.
+ Clcik on elipses next to Override template parameters and change factory name to Prod factory name and AzureKeyVault Url to Prod Url, Azure DataLakeStorage dev account name to Prod account name. Click on Ok and Save.

<img width="995" alt="image" src="https://user-images.githubusercontent.com/84516667/197865546-1650f2eb-4b97-4926-9947-3d689f2dcf81.png">


[Continue >](module04.md)
