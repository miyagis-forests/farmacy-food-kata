# ADR 006: Use AWS as cloud provider
Farmacy Food is not an IT enterprise, and has limited work force to manage the IT infrastructure. 
The organization wants to see quick growth in the number of customers and orders placed. This growth requires scalability
of the running platform.  

## Decision 
The Farmacy Food server-side system will be run on a public cloud. We will use Amazon AWS as the cloud provider, and
deploy the Farmacy Food system preferably using AWS-managed services.

## Rationale 
First off, there are good reasons to deploy on the cloud:
- In the first Kata session, Kwaku himself said he expects to use the cloud.
- These days, virtually all startups that rely on a software solution on the Web use a public cloud infrastructure. Startups don't
have the people and money needed to install and manage physical server machines and VMs on top of those. 
- Microservice-based solutions like the Farmacy Food system uses several different infrastructure elements, such as
web server, container orchestration platform, relational database, NoSQL database, and pub-sub message broker. This
needed technology diversity increases TCO. Using managed services in the cloud alleviates the burden. For example: 
using Kafka on premises requires configuring a cluster of ZooKeeper and Kafka servers, with tons of configuration options. 
It is much easier (for the IT team) to use a managed cloud service, such as AWS MSK or Kinesis.
- On premises infrastructure do not give the elasticity (horizontal scalability) [required by Farmacy Food](../requirements/quality-attribute-rqmts.md).
(Twenty years ago, if your website/service went "viral" you would run to Radio Shack to buy more CPUs and call your ISP 
to increase the link bandwidth. Today, we simply deploy the solution in the cloud.) 

The other aspect, is the choice of AWS:
- The truth is... other cloud providers, such as Microsoft Azure and Google Cloud would provide the variety 
of services that Farmacy Food requires, with equivalent quality and cost.  
- For the sake of the Kata, we picked AWS to be able to illustrate this important architecture perspective: *how your system is
deployed*. The choice of AWS over others is based on our own team familiarity with the platform--one of us is a Certified AWS Developer 
and our organization has a contract with AWS (via a cloud broker).
- Moving forward our suggestion to Farmacy Food is to pick one of the big cloud providers based on the tech skills of your IT team (if you
have an expert in Azure and you are a startup, you just go with Azure, for example). 
 

## Status
Proposed 

## Consequences
- Farmacy Food needs to create an AWS account and hire or train an engineer that is familiar with AWS services.  
- The CI/CD jobs/pipelines should include integration with the cloud provider services. For AWS, this is typically done
via [CloudFormation](https://aws.amazon.com/cloudformation/) (Infrastructure as Code for AWS) and [CodeDeploy](https://aws.amazon.com/codedeploy/).  
