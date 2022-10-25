[Home](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD)

**Workshop Terminology**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

1. **Working/Feature Branch** - This is a short lasting branch where each developer must create to update and save their pipelines and activities.
2. **Collaboration Branch** - This is a long lasing branch and changes from feature branch are merged into this branch. By default, it is main. This is also referred as collaborative branch.
3. **Publish Branch** - Publishing related ARM templates are stored and updated in this branch. By default, it is adf_publish. Azure Data Factory can only have one publish branch at a time.
4. **Pull Request** - In order to merge changes from feature branch to collaboration branch, we need to create pull request. This action helps to do code reviews, raise pull requests and merge changes to collaboration branch.
5. **Commit** - Commit is used to save the changes to local repository. In ADF world, it is saving to local branch.
6. **Azure Resource Manager templates** - Azure Data Factory utilizes Azure Resource Manager templates to store the configuration of your various ADF entities (pipelines, datasets, data flows, and so on)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

**Development Workflow**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

+ Azure Repos Git is configured only in development data factory. The test and production factories shouldn't have a git repository associated with them and should only be updated via an Azure DevOps pipeline or via a Resource Management template. 
+ All developers should have permission to author Data Factory resources like pipelines and datasets.
+ Developer creates a feature branch to update/create pipelines. After a developer is satisfied with their changes, they create a pull request from their feature branch to the main or collaboration branch to get their changes reviewed by peers.
+ After a pull request is approved and changes are merged in the main branch, the changes get published to the development factory. <br />

	![image](https://user-images.githubusercontent.com/84516667/197627738-a8a1fdd5-9270-41b0-b89c-780f1865a4ae.png)
	<img width="569" alt="image" src="https://user-images.githubusercontent.com/84516667/197803750-bfdbbb56-b2e4-4b5f-b5e0-11606fad307e.png">


-----------------------------------------------------------------------------------------------------------------------------------------------------------------
**Release Lifecycle**
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

When the team is ready to deploy the changes to a prod factory, the team goes to their Azure Pipelines release and deploys the development factory to next environment (UAT/Prod). This deployment takes place as part of an Azure Pipelines task and uses Resource Manager template parameters to apply the appropriate configuration.


