**ADF DevOps Workshop**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
**Workshop Summary**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
In this workshop we work on implementing continuous integration and continuous deployment for Azure Data Factory using Azure DevOps. 

Azure Data Factory integrates with both Github and Azure DevOps Git for source control. For this lab, we're focussing on Azure DevOps Git. Main objective of source control is to have collaboration among developers, track changes and maintain history. 

**Source Control Terminology**

1. **Working/Feature Branch** - This is a short lasting branch where each developer must create to update and save their pipelines and activities.
2. **Collaboration Branch** - This is a long lasing branch and changes from feature branch are merged into this branch. By default, it is main. This is also referred as collaborative branch.
3. **Publish Branch** - Publishing related ARM templates are stored and updated in this branch. By default, it is adf_publish. Azure Data Factory can only have one publish branch at a time.
4. **Pull Request** - In order to merge changes from feature branch to collaboration branch, we need to create pull request. This action helps to do code reviews, raise pull requests and merge changes to collaboration branch.
5. **Commit** - Commit is used to save the changes to local repository. In ADF world, it is saving to local branch.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
**🤔 Prerequisites**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
+ An Azure account with an active subscription. Note: If you don't have access to an Azure subscription, you may be able to start with a free account.
+ You must have the necessary privileges within your Azure subscription to create resources, perform role assignments, register resource providers (if required), etc.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
**🧪 Lab Environment Setup**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
+ [Lab Environment](Azure-Data-Factory-CI-CD/Lab-Prerequisites.md)
