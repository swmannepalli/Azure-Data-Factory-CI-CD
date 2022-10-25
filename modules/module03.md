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
+ Let's start with Empty job --> Under Select a template, click on Empty job. Provide Stage name (this is environment name), in this lab it is going to be Prod. 

[Continue >](module04.md)
