
# Sample YAML file to validate and export an ARM template into a build artifact
# Requires a package.json file located in the target repository

trigger:
- master #collaboration branch

pool:
  vmImage: 'ubuntu-latest'

steps:

# Installs Node and the npm packages saved in your package.json file in the build

- task: NodeTool@0
  inputs:
    versionSpec: '14.x'
  displayName: 'Install Node.js'

- task: Npm@1
  inputs:
    command: 'install'
    workingDir: '$(Build.Repository.LocalPath)' #replace with the package.json folder
    verbose: true
  displayName: 'Install npm package'

# Validates all of the Data Factory resources in the repository. You'll get the same validation errors as when "Validate All" is selected.
# Enter the appropriate subscription and name for the source factory.

- task: Npm@1
  inputs:
    command: 'custom'
    workingDir: '$(Build.Repository.LocalPath)' #replace with the package.json folder
    customCommand: 'run build validate $(Build.Repository.LocalPath) /subscriptions/a067d50e-1d0a-4458-b682-a151b84a7371/resourceGroups/zacharyzurlo-dev-rg/providers/Microsoft.DataFactory/factories/zacharyzurlo-dev-adf'
  displayName: 'Validate'

# Validate and then generate the ARM template into the destination folder, which is the same as selecting "Publish" from the UX.
# The ARM template generated isn't published to the live version of the factory. Deployment should be done by using a CI/CD pipeline. 

- task: Npm@1
  inputs:
    command: 'custom'
    workingDir: '$(Build.Repository.LocalPath)' #replace with the package.json folder
    customCommand: 'run build export $(Build.Repository.LocalPath) /subscriptions/a067d50e-1d0a-4458-b682-a151b84a7371/resourceGroups/zacharyzurlo-dev-rg/providers/Microsoft.DataFactory/factories/zacharyzurlo-dev-adf "ArmTemplate"'
  displayName: 'Validate and Generate ARM template'

# Publish the artifact to be used as a source for a release pipeline.

- task: PublishPipelineArtifact@1
  inputs:
    targetPath: '$(Build.Repository.LocalPath)/ArmTemplate' #replace with the package.json folder
    artifact: 'ArmTemplates'
    publishLocation: 'pipeline'