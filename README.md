# Testing Azure Pipelines Conditional Builds 
[![Build Status](https://dev.azure.com/abrig/bedrock_gitops/_apis/build/status/andrebriggs.az-conditional-builds?branchName=master)](https://dev.azure.com/abrig/bedrock_gitops/_build/latest?definitionId=8&branchName=master)

Following instructions at [https://docs.microsoft.com/en-us/azure/devops/pipelines/yaml-schema?view=azure-devops&tabs=schema#triggers](https://docs.microsoft.com/en-us/azure/devops/pipelines/yaml-schema?view=azure-devops&tabs=schema#triggers) 

The top level azure-pipeline.yaml has
```
trigger:
  branches:
    include:
      - master
  paths:
    include:
      - bar/foo/*
    exclude:
      - '**/*.md'
```

- So that means only changes under bar\foo should trigger a build
    - We have confirmed this
- We also added an exclusion on all Markdown files via `'**/*.md'`
    - We have confirmed that ADO doesn't trigger for all *.md in the repo
    - The bug is [here](https://github.com/MicrosoftDocs/vsts-docs/issues/2363)

Let's get more compliCated though. We want to:
* Run a test only when one or more directories are changed
