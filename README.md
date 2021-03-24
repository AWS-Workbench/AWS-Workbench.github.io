
#  AWS Workbench

## What is AWS Workbench?

 **AWS Workbench** is the first [ArchOps](https://en.wikipedia.org/wiki/DevOps#ArchOps) environment for designing and deploying AWS Infrastructure. 

AWS Workbench aims to solves the pain points observed in current cloud architecture design and deployment process like ;

 - **Waterfallish handoffs** between Architects and Cloud DevOps Engineers
 -  Absence of **What you see is What is Deployed** (WYSIWID) view of infrastructure 
 - **Adhoc and obscure changes to infrastructure**  without communication to all stakeholders leading to surprises 
 - **Absence of singular view of cloud inventory** leading to wastage of resources. 
 - **Decreased agility** in deploying newer resources due to effort and ambiguity in translation of design to infrastructure code.
 
 AWS Workbench provides: 
 
 - A **truly visual IDE** for designing AWS infrastructure with auto-generation of deployment templates.
 - **Best practices and patterns** based development
 - **Design level verification** of cloud infrastructure blueprint
 - **Accelerated communication** between Architect and Cloud DevOps
 - **Easy reusability and management** 

AWS Workbench features 

 - Provides an **Integrated Development Environment** (IDE) using [Eclipse Sirius](https://www.eclipse.org/sirius/) to define cloud infrastructure, complete with navigation and drill down tools for ease of organization.
 - Auto-generates infrastructure code for  [AWS’s Cloud Development Kit](https://aws.amazon.com/cdk/) with **smart and secure default values** based on AWS’s best practices. 
 - Reduces the need for hand-written infrastructure code by about 80%
 - Supports generation of blueprints using [AWS Solution Constructs](https://aws.amazon.com/solutions/constructs/) as recommended by AWS’s Solution Architects. 
 - Provides inbuilt support for commonly used AWS services 
 - Enables clear separation of generated code and further manual customization.


## Technologies used 

- Java 
- [Eclipse Sirius](https://www.eclipse.org/sirius/) 
- [AWS’s Cloud Development Kit](https://aws.amazon.com/cdk/)

Knowledge of Java language, working with [Eclipse](https://www.eclipse.org/) and installing plugins in Eclipse IDE is a pre-requisite.  

Solution Architect level understanding of [AWS services](https://aws.amazon.com/products/) and  ability to understand [Javadocs](https://docs.aws.amazon.com/cdk/api/latest/java/index.html) is necessary for effective use of this tool. 

## Installation 

***AWS Workbench depends on multiple softwares and would need about an hour to set it all up.***

### Pre-requisites

- An [AWS Account](https://console.aws.amazon.com/)  and [AWS CLI](https://aws.amazon.com/cli/) 
- [Java 8 or newer](https://www.oracle.com/in/java/technologies/javase-downloads.html) 
- [Apache Maven 3.6.3](https://maven.apache.org/) or newer 
- [Node 10.16.2](https://nodejs.org/) or newer 
- [AWS CDK](https://aws.amazon.com/cdk/) 
> npm install -g aws-cdk 

- [Obeo Designer 11.3](https://www.obeodesigner.com/en/download) or newer 

Install following eclipse plugins in Obeo Designer 
- [Eclipse Web Developer Tools](https://marketplace.eclipse.org/content/eclipse-web-developer-tools-0) 
- [Eclipse Maven Plugin](https://www.eclipse.org/m2e/) 

###  Install AWS Workbench
- Clone this repository 
- Install AWS Workbench plugin from [local zip](UpdateSite.zip) . *(Instructions on how to install eclipse plugins from zip file described [here](https://stackoverflow.com/questions/31553376/eclipse-how-to-install-a-plugin-manually/31553745))*
- Start Obeo Designer and we are good to go  


##  Getting started

1. [Understanding AWS Workbench](docs/understanding-workbench.md)
2. [Quick start](docs/quick-start.md) with a sample project 
3. Creating a [new AWS Workbench project](docs/getting-started.md)


## Roadmap 
- Continuous improvement and addition of new services from AWS 
- Create [Landing Zone](https://aws.amazon.com/solutions/implementations/aws-landing-zone/) and [Control Tower](https://aws.amazon.com/controltower/) constructs
- Extend Workbench to [CDK8S](https://cdk8s.io/)
- Extend Workbench to [Azure](https://azure.microsoft.com/en-in/) and [Google Cloud](https://cloud.google.com/) using [Pulumi](https://www.pulumi.com/)



















