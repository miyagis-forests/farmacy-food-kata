# Customer Pickup Microservice View 
The scope is the operations that the customer can perform in person.
In these scenarios, either the smart fridge or the cashier POS acts as entry points to the system.
 
The interactions include:
- picking up already ordered meals; and
- purchasing meals on the spot and collecting it right away.

This is a microservice architecture. Key patterns used:
- Wrapper (aka Legacy Wrapper, Anticorruption Layer)
- CQRS
- Publish-subscribe (in the event-driven architecture)

![customer pickup microservice view](../images/customer-pickup-microservice-view-primary.png)

## Element Catalog 

#### Customer, Smart Fridge, Cashier POS
- The actual customer (in person), Smart Fridge and ashier POS.

#### Smart fridge management system, Vendor management system
- Systems that provide APIs for querying and managing the state of the smart fridges
and vendor management systems.
- Proprietary technology, managed by third-parties.

#### Smart fridge wrapper, Vendor wrapper
- [Wrapper services](../ADRs/ADR003-wrapper-pattern.md) for interacting with third-party partner systems in the cloud. The goal
 of the wrapper services is to avoid tight coupling between Farmacy Food business logic implementation and 
 the specifics of each third-party system.

#### Pick-up transaction updater
- A batch program that queries the Smart Fridge and Vendor management systems for updates and
posts them on the Inventory and Order topics for later handling by the `Inventory command` and
`Order processing` services.

#### Inventory Command
- Reactive service (topic susbscriber) that handles commands updating the inventory.

#### Order processing 
- Reactive service (topic susbscriber) responsible for processing events about orders.


## Behavior
- N/A.
 
## Related ADRs 
- [CQRS pattern](../ADRs/ADR004-cqrs-pattern.md)
- [Wrapper pattern](../ADRs/ADR003-wrapper-pattern.md)

## Related Views
- [Order - microservice and EDA view](../architecture/order-runtime-view.md) 
