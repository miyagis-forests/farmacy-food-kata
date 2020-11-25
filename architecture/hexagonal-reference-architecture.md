# Hexagonal Reference Architecture View 
This view describes the [hexagonal reference architecture](https://alistair.cockburn.us/hexagonal-architecture/) for a typical bounded context in the Farmacy Food system. The scope is interactions between external components (outside components) and the Farmay Food bounded contexts. These interactions are made by adapters that isolate the application and domain layers. 

![Replenish runtime view](../images/hexagonal-reference-architecture.png)

## Element Catalog 

#### REST Adapter
- Handles the requests from outside components by implementing “controllers” that receive HTTP methods like GET, POST, PUT and DELETE.
#### Application + Domain 
- Application elements are called from adapters and provide communication with the domain. 
- In general, domain objects cannot leak outside of the domain area. Ordinarily, domain objects are wrapped in DTO (Data Transfer Object) and returned to outside elements.
#### Batch Adapter
- Executes scheduled tasks
- Typically, these tasks pool components like REST services or datasoruces, for example,  to provide data replication between command sources and query sources, or communication to third party systems by wrapper services to receive or send commands. 

## Behavior
- N/A.
 
## Related ADRs 
- [BFF pattern](../ADRs/ADR002-bff-pattern.md)
- [Wrapper pattern](../ADRs/ADR003-wrapper-pattern.md)
- [Microservice pattern](../ADRs/ADR004-cqrs-pattern.md)


## Related Views
- [Context Diagram](context-diagram.md)
- [AWS Deployment view](aws-deployment-view.md)
