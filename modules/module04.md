------------------------------------------------------------------------------------------------------------------------------------------------------------
**Test Continuous Deployment**
------------------------------------------------------------------------------------------------------------------------------------------------------------
[< Previous Module](module03.md) - [Home](https://github.com/swmannepalli/Azure-Data-Factory-CI-CD)

🤔 Prerequisites
---------------------------------------------------------------------------------------------------------------------------------------------------------

You need to complete [Lab Environment Setup](module00.md)&ensp;  [Create a project in Azure DevOps](module01.md) &ensp;  [Data Factory Development Workflow](module02.md)  &ensp; [Release Lifecycle](module03.md)

---------------------------------------------------------------------------------------------------------------------------------------------------------

+ Now, that the deployment workflow and creation of release pipelines is complete, let's test Continuous deployment part.
+ In the previous section, we have included adf_publish branch to our Continuous deployment trigger, so whenever changes are published to adf_publish branch an automatic deployment is done and code is pushed to Prod Data Factory.
+ Go to Data Factory studio, make any change to the pipeline. For example, changing name of the pipeline. Validate the change and make sure there are no errors and Publish it (assuming you're in main branch). This is only for testing purpose. It is not recommended to make any changes in main branch directly.
+ Publish the changes by clicking on Publish button. As soon as ARM template generation completes, go to Azure DevOps project --> Pipelines --> Releases. You should see build is initiated automatically.

<img width="1020" alt="image" src="https://user-images.githubusercontent.com/84516667/197869665-1e1aac53-33ec-44b2-a4dd-c643a4ea4fda.png">

+ Once build completes successfully, go to Prod Data Factory and ensure all dev artifacts are deployed in Prod.
