**Workshop Terminology**

1. **Working/Feature Branch** - This is a short lasting branch where each developer must create to update and save their pipelines and activities.
2. **Collaboration Branch** - This is a long lasing branch and changes from feature branch are merged into this branch. By default, it is main. This is also referred as collaborative branch.
3. **Publish Branch** - Publishing related ARM templates are stored and updated in this branch. By default, it is adf_publish. Azure Data Factory can only have one publish branch at a time.
4. **Pull Request** - In order to merge changes from feature branch to collaboration branch, we need to create pull request. This action helps to do code reviews, raise pull requests and merge changes to collaboration branch.
5. **Commit** - Commit is used to save the changes to local repository. In ADF world, it is saving to local branch.
6. **Azure Resource Manager templates** - Azure Data Factory utilizes Azure Resource Manager templates to store the configuration of your various ADF entities (pipelines, datasets, data flows, and so on)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
