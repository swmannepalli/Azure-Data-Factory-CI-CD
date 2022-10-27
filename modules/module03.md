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

Once the pipeline is created, the pipeline name is automatically configured with the project name. You can rename it to “AzureDataFactory-CI” to give a more meaningful name. 

<img width="931" alt="image" src="https://user-images.githubusercontent.com/84516667/198374612-86ea6920-a2a6-4adb-8d92-7ba7c3ad6fdf.png">

---------------------------------------------------------------------------------------------------------------------------------------------------------

**Testing development lifecycle** <br />

---------------------------------------------------------------------------------------------------------------------------------------------------------

+ Developers should perform unit test cases in their feature branch to make sure there are no errors and the code is matching to their requirements. In this case, click on Validate all to check there are no errors in the pipeline created above.  <br />
+ To merge changes back to Collaboration branch, expand the feature1 branch on the left top, and click on Create Pull Request. This will take you to the Azure DevOps page.  <br />
+ Provide Title and add reviewers if required. This is recommended approach so there are some other users who can validate your branch work to prevent any errors in main/collaboration branch. For this lab, you can skip it and click on Create and Complete. A pop up window appears, and it is best approach to delete feature1 branch after merging which helps in keeping the commit history and repo clean. Click on Complete Merge.  <br />

+ This will automatically trigger the pipeline as there is a commit made to the master branch via pull request. On reviewing the Pipelines, you should see that the AzureDataFactory-CI pipeline is triggered as a result of merging the Pull request and completed successfully.

<img width="788" alt="image" src="https://user-images.githubusercontent.com/84516667/198375182-30ad8a5d-e875-44ea-8fa6-4cd2a9f938a5.png">

On reviewing the run, you should see something like below which shows that an artefact is published and clicking that, we should be able to view the files present in that.

<img width="1009" alt="image" src="https://user-images.githubusercontent.com/84516667/198360586-7d405c96-5822-4602-bc5f-7b4d739e2dc9.png">

<img width="861" alt="image" src="https://user-images.githubusercontent.com/84516667/198360058-f8873426-6c25-485a-bcb3-1870d6f2bf41.png">

The completes setting up our build pipeline section. In the next section, we will be creating a release pipeline to deploy this on to Production.

[Continue >](module04.md)
