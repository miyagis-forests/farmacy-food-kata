This is the github repo for the solution created by team Miyagi's Little Forests for the O'Reilly Architecture Kata. It contains a proposed architecture for [Farmacy Food](https://www.farmacyfood.com/).

# Farmacy Food system

### Requirements

This section brings the elicited requirements that served as foundation to the decisions in this proposal. 

- [Functional requirements](requirements/functional-rqmts.md)
- [Quality attribute requirements](requirements/quality-attribute-rqmts.md)

### Architecture

The architectural views below present the services designed to support Farmacy Food's requirements. They are divided
in five specific views which intend to best group them according to their functionality and interactions.
 
- [Customer Account Management - microservice view](architecture/user-account-mgmt-runtime-view.md)
- [Catalog - microservice view](architecture/catalog-runtime-view.md)
- [Order - microservice and EDA view](architecture/order-runtime-view.md)
- [Customer at pick-up location - microservice and EDA view](architecture/customer-pickup-microservice-view.md)
- [Replenisher - microservice and EDA view](architecture/replenish-runtime-view.md) 

### ADRs

The recording of the architectural decisions regarding the proposed design, including their context and rationale.

- [Payment gateway](ADRs/ADR001-payment-gateway.md)
- [BFF pattern](ADRs/ADR002-bff-pattern.md)
- [Wrapper pattern](ADRs/ADR003-wrapper-pattern.md)
- [CQRS pattern](ADRs/ADR004-cqrs-pattern.md)

<sub>***Note***: *we used [this ADR template](https://github.com/pmerson/ADR-template/blob/master/ADR-template.md). It is slightly 
different from the template presented by Neal during the first Kata session. 
The justification is in the [template repo README file](https://github.com/pmerson/ADR-template/blob/master/README.md#why-this-template).*</sub>

--------------------------

### Backlog
Pending design activities for a hypothetical future sprint. :^)
- Better record the quality attribute requirements (aka non-functional requirements). Requires talking to Kwaku and 
other Farmacy Food stakeholders.  
- Create a deployment architecture view to describe design aspects, such as:
    - cloud deployment choices, for example: use Amazon EKS
    - containerization (e.g., pod placement, K8S cluster definition)
    - scalability settings
    - log consolidation
    - monitoring and tracing
- Create architecture views to show the structure of the implementation units. Examples of information in such views:
    - how is code to be structured in layers (hexagonal aka ports and adapter would be a good option…)
    - entities and VOs that form aggregates (or equivalent if not using DDD modeling)
    - domain events and event hierarchies  
- Write ADR for use of CQRS pattern
- Write ADR for using a microservice architecture style
- Write ADR for using an event-driven architecture for order processing.
- Add the description of components that are missing in the element catalogs of the architecture views.    

--------------------------

## *About the team Name*
*Miyagi's Little Forests is certainly an unusual name for a dev team. The name has both a pop culture and an academic reference:* 
- Mr. Miyagi is the shy Karate master in the 1984 "The Karate Kid" film. In the movie, which inspired a generation of then teenagers including the members of this team, Mr. Miyagi teaches the young Daniel-san the ancient art of Karate. The teaching of this martial art is anchored on Katas. Hence the nuanced connection to our architecture challenge.
- In a seminal 1976 [paper](https://www.ics.uci.edu/~andre/ics223w2006/deremerkron.pdf), Frank DeRemer and Hans Kron described like this the concern that 15 years later would drive the advent of the *software architecture* field: "However, current languages discourage the accurate recording of the overall solution structure; they force us to write programs in which we are so preoccupied with the trees that we lose sight of the forest, as do the readers of our programs!" For long, we have used the ability to see the forest and not only the trees as a metaphor for thinking the software architecture. 
- In The Karate Kid, Miyagi and Daniel-san form a team and open a store called *Miyagi's Little Trees*. So, paying homage to the movie and embracing the architecture metaphor, we are team **Miyagi's Little Forests**. 

![Miyagi and Daniel-san](images/Miyagi-and-Daniel-san.jpg)
