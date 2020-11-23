# AWS Deployment View 
This view shows how the server-side components of the Farmacy Food system can be deployed on the AWS platform. 

![AWS deployment view](../images/aws-deployment-view-primary.png)


## Element Catalog 

#### EKS
- [Elastic Kubernetes Service](https://aws.amazon.com/eks/features/) makes it easy to run your system to run on a Kubernetes (K8S)
cluster in the cloud. Many of the tasks related to creating, configuring, and monitoring K8S nodes and clusters is done for you.
- EKS runs on EC2 instances inside a private network (VPC) that you define within AWS.
      
 
## Related ADRs 
- [AWS as the cloud provider](../ADRs/ADR006-aws-as-cloud-provider.md)

## Related Views
- [Customer Account Management - microservice view](user-account-mgmt-microservice-view.md)
- [Catalog - microservice view](catalog-microservice-view.md)
- [Order - microservice and EDA view](order-microservice-eda-view.md)
- [Catalog - microservice view](catalog-microservice-view.md)
- [Replenisher - microservice and EDA view](replenish-microservice-eda-view.md) 
- [Hexagonal reference architeture view](hexagonal-reference-architecture.md) 
