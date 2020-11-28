# DDD Context Map

<!-- Short description of the scope and nature of this architecture view. --> 

The following architecture view is a [DDD Context Map](https://learning.oreilly.com/library/view/patterns-principles-and/9781118714706/c07.xhtml). 
It shows how the Farmacy Food system is broken up into bounded contexts (BCs) and how they interact with each other. 

![DDD Context Map](../images/ddd-context-map2.png)

![DDD Context Map](../images/ddd-context-map-key.png)

## Element Catalog 

<!--
#### Element X
- info
- info
-->

#### Subdomain
- TODO closer shot
- info

#### Bounded Context
- TODO closer shot
- info

#### Conformist (BC Relationship)
- U/D
- TODO closer shot

#### Anticorruption Layer - ACL (BC Relationship)
- U/D
- TODO closer shot

#### Types of Technical Integrations between BCs
- TODO closer shot
- Via Event
    - x
- Via REST API
    - x
- Via Data Replication
    - x

## Behavior
- N/A.
 
## Related ADRs 
- [Microservice pattern](../ADRs/ADR004-cqrs-pattern.md)
- [Wrapper pattern](../ADRs/ADR004-wrapper-pattern.md)

<!--
- [AWS as the cloud provider](../ADRs/ADR006-aws-as-cloud-provider.md)
- [BFF pattern](../ADRs/ADR002-bff-pattern.md)cu
- [CQRS pattern](../ADRs/ADR005-cqrs-pattern.md)
- [Payment gateway](../ADRs/ADR002-payment-gateway.md)
-->

## Related Views
- [Context Diagram](context-diagram.md)
- [User Account Management - microservice view](user-account-mgmt-microservice-view.md)
- [Catalog - microservice view](catalog-microservice-view.md)
- [Order - microservice and EDA view](order-microservice-eda-view.md)
- [Customer at Pick-up Location Microservice and EDA View](customer-pickup-microservice-eda-view.md)
- [Replenisher - microservice and EDA view](replenish-microservice-eda-view.md)

<!--
- [AWS Deployment view](aws-deployment-view.md)
- [Hexagonal reference architeture view](hexagonal-reference-architecture.md)
--> 
