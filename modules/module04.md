------------------------------------------------------------------------------------------------------------------------------------------------------------
**Test Continuous Integration and Continuous Deployment**
------------------------------------------------------------------------------------------------------------------------------------------------------------
[< Previous Module](module03.md) - [Home](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD)

🤔 Prerequisites
---------------------------------------------------------------------------------------------------------------------------------------------------------

You need to complete [Lab Environment Setup](module00.md)&ensp;  [Create a project in Azure DevOps](module01.md) &ensp;  [Data Factory Development Workflow](module02.md)  &ensp; [Release Lifecycle](module03.md)

---------------------------------------------------------------------------------------------------------------------------------------------------------

+ Now, that the development workflow and creation of release pipelines is complete, let's test CI/CD.
+ Go to Data Factory studio, refersh page as feature1 branch no longer exists (we deleted this branch as part of our create pull request - merge changes to master in module02) create another feature branch.

<img width="924" alt="image" src="https://user-images.githubusercontent.com/84516667/199150700-3e4e7f18-6c2a-4359-84dc-2b7062af664b.png">

+ Make some changes to pipeline. For example, changing name of the pipeline. Validate the change and make sure there are no errors, Save all. Create a pull request by clicking on drop down next to branch name.
+ This will take you to Azure DevOps page, click on Create, Complete and Complete Merge. This will start the build pipeline to gather artifacts and create arm templates.

<img width="797" alt="image" src="https://user-images.githubusercontent.com/84516667/198489443-741d9cfc-a508-45e1-ae38-299192bc9b17.png">

+ As we've enabled continuous deployment trigger whenever changes are made to master branch, release pipeline for Dev starts automatically. Once that succeeds, approvers will get notification to approve Prod build.
+ Once approvals are done, prod deployment will start.
+ Once deployment completes successfully, go to Prod Data Factory and ensure all dev artifacts are deployed in Prod.

<img width="647" alt="image" src="https://user-images.githubusercontent.com/84516667/198491298-8714bb9e-6712-455d-95fb-09078e11fa95.png">


