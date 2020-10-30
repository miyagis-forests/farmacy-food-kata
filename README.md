This is the github repo for the solution created by team Miyagi's Little Forests for the O'Reilly Architecture Kata. It contains a proposed architecture for [Farmacy Food](https://www.farmacyfood.com/).

# Farmacy Food system

### Requirements
- [Functional requirements](requirements/farmacy-food-requirements.md)
- Quality attribute requirements

### Architecture
- [Customer Account - microservice view](architecture/user-account-mgmt-runtime-view.md)
- Customer at pick-up location - runtime view
- Replenisher - runtime view

### ADRs
- [Payment gateway](ADRs/ADR001-payment-gateway.md)
- [BFF pattern](ADRs/ADR002-bff-pattern.md)
- [Wrapper pattern](ADRs/ADR003-wrapper-pattern.md)
- [CQRS pattern](ADRs/ADR004-cqrs-pattern.md)

### Backlog
Pending design activities for a future sprint. :^)
- Create a deployment architecture view to describe design aspects, such as:
    - cloud deployment choices, for example: use Amazon EKS
    - containerization (e.g., pod placement, K8S cluster definition)
    - scalability settings
    - log consolidation
    - monitoring and tracing
- Create architecture views to show the structure of the implementation units. Examples of information in such views:
    - how is code to be structured in layers (hexagonal aka ports and adapter would be a good option...)
    - entities and VOs that form aggregates (or equivalent if not using DDD modeling)
    - domain events and event hierarchies  
- Write ADR for use of CQRS pattern
- Write ADR for using a microservice architecture style
- Write ADR for using an event-driven architecture for order processing.

--------------------------

## *About the team Name*
*Miyagi's Little Forests is certainly an unusual name for a dev team. The name has both a pop culture and an academic reference:* 
- Mr. Miyagi is the shy Karate master in the 1984 "The Karate Kid" film. In the movie, which inspired a generation of then teenagers including two members of this team, Mr. Miyagi teaches the young Daniel-san the ancient art of Karate. The teaching of this martial art is anchored on Katas. Hence the nuanced connection to our architecture challenge.
- In a seminal 1976 [paper](https://www.ics.uci.edu/~andre/ics223w2006/deremerkron.pdf), Frank DeRemer and Hans Kron described like this the concern that 15 years later would drive the advent of the *software architecture* field: "However, current languages discourage the accurate recording of the overall solution structure; they force us to write programs in which we are so preoccupied with the trees that we lose sight of the forest, as do the readers of our programs!" For long, we have used the ability to see the forest and not only the trees as a metaphor for thinking the software architecture. 
- In The Karate Kid, Miyagi and Daniel-san form a team and open a store called *Miyagi's Little Trees*. So, paying homage to the movie and embracing the architecture metaphor, we are team **Miyagi's Little Forests**. 

![Miyagi and Daniel-san](images/Miyagi-and-Daniel-san.jpg?raw=true)
