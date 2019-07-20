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
```

So that means only changes under bar\foo should trigger a build

Let's get more complciated though. We want to:
* Run a test only when one or more directories are changed
