
🤔 Prerequisites
---------------------------------------------------------------------------------------------------------------------------------------------------------

+ Account and Organization created in Azure Devops. 
+ If not, follow [this](https://learn.microsoft.com/en-us/azure/devops/user-guide/sign-up-invite-teammates?view=azure-devops) tutorial to sign up. You can provide your Non-Prod credentials and can skip step 1.

---------------------------------------------------------------------------------------------------------------------------------------------------------

## :dart: Objectives
---------------------------------------------------------------------------------------------------------------------------------------------------------

+ Adding Add Non-Prod Subscription to existing organization
+ Creating Azure DevOps project
+ Adding Service connection to Non-Prod subscription

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

+ Provide project name that will be used for this workshop and check other settings in screenshot below.

<img width="322" alt="image" src="https://user-images.githubusercontent.com/84516667/198498472-db51107b-79bd-474f-bb94-976fffe66e2f.png">



**Step 3: Add Service connection to Non-Prod subscription**
---------------------------------------------------------------------------------------------------------------------------------------------------------

