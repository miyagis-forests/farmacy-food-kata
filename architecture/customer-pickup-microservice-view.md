# Customer Pickup Microservice View 
The scope is the operations that the customer can perform having the smart fridge or the POS cashier as
entry point. These interactions include picking up an already ordered food and purchasing an item on
the spot and retrieving it right away.

This is a microservice architecture. Key patterns used:
- Wrapper (aka Legacy Wrapper, Anticorruption Layer)
- CQRS
- Publish-subscribe (in the event-driven architecture)

![customer pickup microservice view](../images/customer-pickup-microservice-view-primary.png)

## Element Catalog 

#### Customer
- x

#### Smart Fridge
- x

#### POS Cashier
- x

#### Smart fridge management system (?)
- x

#### Vendor management system (?)
- x

#### Wrappers (?)
- x

#### Pick-up transaction updater
- x

#### Inventory Command (?)
- x

#### Order processing (?)
- x


## Behavior
- N/A.
 
## Related ADRs 
- [CQRS pattern](../ADRs/ADR004-cqrs-pattern.md)
- what else?

## Related Views
- TO-DO: link to order view 
