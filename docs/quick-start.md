

# AWS Workbench Quick Start Guide

This guide assumes that you have [set up](../README.md#installation) Obeo Designer successfully, cloned this repository and installed the workbench plugin. 


## Import sample project 

- Open Obeo Designer.
- Import ```ArchOpsDemo``` project under ```sample``` folder into you Obeo workspce. 
- Click [here](../images/getting-started-images/import-project.gif) to see how to import the project. 

## Generate Java code 

- Open the ```ArchOpsDemo``` diagram .
- On the Canvas ```Right Click -> Generate -> Code ```
- On the newly created project ```Right Click -> Maven -> Update Project```
- Click [here](../images/getting-started-images/export-code.gif) to see how to generate java code.

## Generate Cloud formation script and deploy

- Open Terminal 
- Navigate to the directory of the newly formed project
- Run commands ```mvn package``` and then ```cdk synth```. 
- Cloud formation script will be generated in the ```cdk.out``` folder in the project directory
- Click [here](../images/getting-started-images/generate-cf.gif) to see how to generate cloud formation script.
- The generated script can be deployed to AWS account using ```cdk deploy``` . 
       




