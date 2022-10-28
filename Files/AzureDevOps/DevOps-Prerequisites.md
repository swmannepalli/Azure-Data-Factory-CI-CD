
🤔 Prerequisites
---------------------------------------------------------------------------------------------------------------------------------------------------------

+ Account and Organization created in Azure Devops. 
+ If not, follow [this](https://learn.microsoft.com/en-us/azure/devops/user-guide/sign-up-invite-teammates?view=azure-devops) tutorial to sign up. You can provide your Non-Prod credentials and can skip step 1.

---------------------------------------------------------------------------------------------------------------------------------------------------------

## :dart: Objectives
---------------------------------------------------------------------------------------------------------------------------------------------------------

1. Adding Add Non-Prod Subscription to existing organization - All resources required for this lab will be created in Non-Prod. 
2. Creating Azure DevOps project
3. Create ARM Service connection to Non-Prod subscription - A Service Connection is required for Azure DevOps Continuous Build and Continuous Release Pipelines to talk to external and remote services and execute tasks. If you want to understand what happens when you create an ARM serice connection, check [this](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/azure-rm-endpoint?view=azure-devops#what-happens-when-you-create-an-arm-service-connection)

---------------------------------------------------------------------------------------------------------------------------------------------------------
**Step 1: Add Non-Prod Subscription**
---------------------------------------------------------------------------------------------------------------------------------------------------------

These steps are for individuals who already have their Organization linked to Prod directory.

+ Login to https://dev.azure.com to open Azure DevOps and go to Organization settings (bottom left)

<img width="472" alt="image" src="https://user-images.githubusercontent.com/84516667/198496246-ad47fe65-9c7b-4a49-8aa8-cb0aea3a6735.png">

+ Under General, click on Azure Active Directory and click on Switch directory. Under Azure Active Directory drop-down, select Microsoft Non-Production and click on Connect.

<img width="923" alt="image" src="https://user-images.githubusercontent.com/84516667/198496987-0bd052cd-992e-471d-8a87-a6528697cef8.png">

+ You've to sign out and sign in back with same account credentials. Now, your organization is connected to the Microsoft Non-Production directory.

---------------------------------------------------------------------------------------------------------------------------------------------------------
**Step 2: Create Azure DevOps Project**
---------------------------------------------------------------------------------------------------------------------------------------------------------
+ Login to https://dev.azure.com to open Azure DevOps. Make sure your organization is selected on top left side. Click on New project.

<img width="940" alt="image" src="https://user-images.githubusercontent.com/84516667/198498295-2eb40fe9-ec3c-43fb-a846-e2f47d65a29d.png">

+ Provide project name that will be used for this workshop and check other settings in screenshot below. Click on Create.

<img width="322" alt="image" src="https://user-images.githubusercontent.com/84516667/198498472-db51107b-79bd-474f-bb94-976fffe66e2f.png">


**Step 3: Create ARM Service connection to Non-Prod subscription**
---------------------------------------------------------------------------------------------------------------------------------------------------------

+ Go to the project created above, and select Project settings.

<img width="149" alt="image" src="https://user-images.githubusercontent.com/84516667/198499277-9d01c1e0-e001-4642-b6bd-cf2989be15a5.png">

+ Under Pipelines, select Service connections --> New service connection

<img width="908" alt="image" src="https://user-images.githubusercontent.com/84516667/198499398-eb353a36-274d-4cbe-86c4-8b3647e217a2.png">

+ Select Azure Resource Manager, clcik on Next. Select Service principal (automatic) and click on Next.
+ Select Scope level as Subscription, select Non-prod subscription. Leave Resource group value as empty as we don't want to limit this connection to one single resource group.
+ Provide Service connection name and click on Save.

<img width="248" alt="image" src="https://user-images.githubusercontent.com/84516667/198500438-ee545df0-f98e-4bbe-9715-7bf2026cd9a3.png">

