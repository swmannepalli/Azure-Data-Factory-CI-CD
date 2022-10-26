**Module 03 - Release Lifecycle**
---------------------------------------------------------------------------------------------------------------------------------------------------------

[< Previous Module](module02.md) - [Home](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD) - [Next Module >](module04.md)

🤔 Prerequisites
---------------------------------------------------------------------------------------------------------------------------------------------------------

You need to complete [Module 00 - Lab Environment Setup](module00.md), [Module 01 - Create a project in Azure DevOps](module01.md) and [Module 02 - Data Factory Development Workflow](module02.md)

---------------------------------------------------------------------------------------------------------------------------------------------------------

**Creating Release Pipeline**
---------------------------------------------------------------------------------------------------------------------------------------------------------

Now that we've completed development lifecycle where publish branch has all the artifacts, we need to create release pipeline to deploy changes to Prod environment.

**Release Pipeline Steps:**

<img width="929" alt="image" src="https://user-images.githubusercontent.com/84516667/197865729-3543728f-3570-468d-a17e-583a44c9406b.png">

**Step 1 - Create a release pipeline:**

+ Go to Azure DevOps project --> Pipelines --> Releases. Click on New pipeline
+ Let's start with Empty job --> Under Select a template, click on Empty job. 

**Step 2 - Define a stage name:**

+ Provide Stage name (this is environment name), in this lab it is going to be Prod. Click on Save and Ok.
<img width="845" alt="image" src="https://user-images.githubusercontent.com/84516667/197841827-e1efabef-a750-415d-bb9a-332450313b5a.png">

**Step 3 - Add Artifacts:**

+ Click on Add an artifact, this we where we provide details about our dev environment artifacts. For Source type, select Azure Repos Git and select Project, repository. Select Default branch as adf_publish which is the branch to checkout. You can have separate branch created for this as well. Click on Add.

**Step 4 - Create ARM Template Deployment Task:**

+ Now, we need to add a task to provide destination environment details i.e., Prod Data Factory environment. Click on the 1 job, 0 task under Prod Stage, click on '+' next to Agent job and search for Arm Template deployment and click on add. Select the job to fill out the configurations. 
+ For Azure Resource Manager Connection, select your subscription where Prod Data Factory is deployed and click on Authorize.
+ Once the authoriztion is complete, select the Subscription, Resource group and Location of Prod Data Factory.
+ For Template, browse and select ARMTemplateForFactory file.
+ For Template parameters, browse and select ARMTemplateParametersForFactory file.
+ Clcik on elipses next to Override template parameters and change factory name to Prod factory name and AzureKeyVault Url to Prod Url, Azure DataLakeStorage dev account name to Prod account name. Click on Ok and Save.

<img width="995" alt="image" src="https://user-images.githubusercontent.com/84516667/197865546-1650f2eb-4b97-4926-9947-3d689f2dcf81.png">

**Step 5 - Define Trigger for Continuous Deployment :**

+ On the Pipeline tab, click on  &ensp; <img width="25" alt="image" src="https://user-images.githubusercontent.com/84516667/197866710-9b0b9d6c-db3d-4ef9-914d-c20367e09eb5.png">  &ensp; icon in Artifacts section, toggle Continuous deployment trigger to enable it.
+ Under Branch filters, click on Add to include a branch from where a release will be triggered only if the Git push contains a commit on the specified branch. For example, selecting "main" will trigger a release for a Git push which contains one or more commits to the main branch. To trigger a release for any commit to branches under features/, enter "features/*". To trigger a release for commits to all branches, enter "*". Note that all specified filters will be OR'ed. For example, an artifact matching at least one filter condition would be sufficient to trigger a release.
+ Select adf_publsih branch and click on Save and Ok. 
+ Now, everytime we publish the code from Data Factory, arm template will be updated in adf_publish branch which will trigger deployment to Prod Data Factory.

<img width="468" alt="image" src="https://user-images.githubusercontent.com/84516667/197867697-bcdfbfd0-58b3-45bf-a180-8a77c37f364d.png">

[Continue >](module04.md)
