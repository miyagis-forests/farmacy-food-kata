# AWS Deployment View 
This view shows how the server-side components of the Farmacy Food system can be deployed on the AWS platform. Useful links:
- This [web page](https://towardsdatascience.com/kubernetes-application-deployment-with-aws-eks-and-ecr-4600e11b2d3c) has
instructions on how to configure a K8S cluster on EKS using docker images in ECR.
- This [AWS doc page](https://docs.aws.amazon.com/eks/latest/userguide/eks-networking.html) describes restrictions and
guidelines for EKS topology.   

![AWS deployment view](../images/aws-deployment-view-primary.jpg)


## Element Catalog 

#### K8S node (EC2 instance)
- The [Elastic Kubernetes Service](https://aws.amazon.com/eks/features/) (EKS) allows you to easily configure 
a Kubernetes (K8S) cluster in the AWS cloud. 
- A K8S cluster has *worker nodes* that run your application as docker containers that are deployed in *pods*. 
In EKS, these nodes are EC2 instances declared as part of a *node group* that is configured inside your VPC. 
- The nodes in an EKS cluster should be in 2+ availability zones (AZs). The diagram illustrates two AZs.  
- We'll use the EKS cluster to run the following types of components seen in the microservice and EDA views:
  - microservices that contain REST services
  - microservices that contain reactive services (topic subscribers)
  - batch programs
  
![AWS deployment view](../images/components-on-k8s.png)

#### EKS control plane
- This element represents K8S control plane nodes that oversee the execution of pods in the worker nodes. More 
information [here](https://kubernetes.io/docs/concepts/overview/components/).
- The EKS control plane executes under an AWS-managed account. That's why it's represented outside the Farmacy Food VPC.
      
#### Amazon ECR 
- The [Amazon Elastic Container Registry](https://aws.amazon.com/ecr/) (ECR) is a docker container registry that 
Farmacy Food will use within AWS to store the several docker images comprising the Farmacy Food system.
- ECR is an alternative to docker-hub. 
- It's a fully managed service provided by AWS.
      
#### RDS primary instance, RDS standby replica
- [RDS](https://aws.amazon.com/rds/) is a relational database managed service by AWS. (There are other options for the 
database server to be used, such as  Oracle, PostgreSql, Aurora, but MySQL is eligible for AWS free tier and should 
reduce the upfront investment to set up and explore an AWS dev environment.)       
- Should be configured as a RDS cluster with the multi-AZ deployment option for increased availability. In this case there's a primary instance,
and a standby replica that is kept in sync automatically after a write operation on the primary. 
- The Farmacy Food System will use RDS with MySQL as the primary read-write data store to persist different types of data. 
For example, the **Inventory** database seen below will be configured as a set of tables in RDS.

![AWS deployment view](../images/inventory-db-symbol.png)    

#### ElasticSearch
- The [Elasticsearch service on AWS](https://aws.amazon.com/elasticsearch-service/) (ES) is a fully managed text-based NoSQL 
database service that the Farmacy Food system will use for query views in different microservices.
- There will be an ES *domain* for Farmacy Food. This ES domain should use the Farmacy Food VPC to enable automatic
secure communication between application components (microservices and batch programs) and the ES nodes. 
- The ES domain should use multi-AZ deployment for increased availability. 
- The Farmacy Food System will use ES as the *query view* to be accessed by microservices that need to only read data. 
For example, the **Inventory Query View** database seen below will be configured using ES.

![AWS deployment view](../images/inventory-query-view-db-symbol.png)    

#### Kafka (AWS MSK)
- The [Amazon managed Kafka service](https://aws.amazon.com/msk/) (MSK) is a fully-managed Kafka broker cluster that 
  supports publish-subscribe channels (called topics).
- Components that send messages (producers aka publishers) and receive messages (consumers aka subscribers) can be 
implemented using various languages and frameworks. For example, we can use the [spring cloud AWS](https://www.baeldung.com/spring-cloud-aws-messaging)
framework.  
- The various topics seen in the EDA architecture views shall be configured in the MSK cluster with minimum replication factor of 3.
- The MSK service automatically provides multi AZ deployment of the Kafka cluster for enhanced availability and throughput. 

![AWS deployment view](../images/topic-symbol.png)
 
#### Availability zone 1, Availability zone 2
- An [availability zone](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-availability-zones) 
(AZ) is a data center with its own power supply and network connectivity.
- AZs are located within regions. Deploying cloud services/resources in 2+ AZs in the same region is the basic mechanism 
for improved availability due to automatic failover.    
 
#### Public subnet 1 and 2, private subnet 1 and 2
- A [subnet](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) is a range of IP addresses within 
a [virtual private cloud](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html) (VPC).
- Public subnets 1 and 2 are visible to the Internet via an AWS internet gateway.
- Private subnets 1 and 2 are not visible to the Internet. They can be connected to the Farmacy Food corporate LAN (not shown in the diagram). 
- Although RDS and ES are configured within private subnets as a measure to protect them from unauthorized access.  

#### Internet gateway 
- The [Internet gateway](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html) is attached to your VPC. Via
route tables it allows inbound and outbound traffic from/to the Internet to reach the elements in the public subnets. (Also has routes for private subnets for internal access.)
- A more sophisticated alternative would be to use an API gateway, which has special features such as authentication, authorization, 
request throttling, and caching. 


## Behavior
N/A
 
## Related ADRs 
- [AWS as the cloud provider](../ADRs/ADR006-aws-as-cloud-provider.md)
- [CQRS pattern](../ADRs/ADR005-cqrs-pattern.md)

## Related Views
- [User Account Management - microservice view](user-account-mgmt-microservice-view.md)
- [Catalog - microservice view](catalog-microservice-view.md)
- [Order - microservice and EDA view](order-microservice-eda-view.md)
- [Catalog - microservice view](catalog-microservice-view.md)
- [Replenisher - microservice and EDA view](replenish-microservice-eda-view.md) 
- [Hexagonal reference architecture view](hexagonal-reference-architecture.md) 
