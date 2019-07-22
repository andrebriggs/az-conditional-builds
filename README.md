# Testing Azure Pipelines Conditional Builds 

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
- We also added an exclusion on all Markdown files via `'**/*.md'`

Let's get more compliCated though. We want to:
* Run a test only when one or more directories are changed
