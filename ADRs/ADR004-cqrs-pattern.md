# ADR 004: Use a CQRS Pattern
We have a microservice architecture with several REST services that write and read data. 
Sometimes it's difficult to design those services to do both tasks efficiently.
In Farmacy Food, the design of writes (commands) focus on the integrity of data and business rules, and the design of reads (queries) takes care of performance (response time). 

## Decision 
We will use the [CQRS pattern](https://udidahan.com/2009/12/09/clarified-cqrs/) and have many commands and queries as well as tasks (batch components) to synchronize the data between data that are persisted from commands to data on source of queries. For instance, we have commands, queries and data synchronization for:
- Inventory
- Orders
- Subscription


## Rationale 
In Farmacy Food the [CQRS pattern](https://udidahan.com/2009/12/09/clarified-cqrs/) is used to solve problems with performance (response time) on queries. For instance:
- The order data are persisted through commands that are called from events on Kafka topics
- After the payment of the order, a synchronization task does the job of sync data to a query source  with a model designed for performance (i.e NoSQL with a desnormalized view)
- Finally,  the customer query history of orders in a fast track model        

## Status
Proposed 

## Consequences
- Need to monitor synchronization tasks, acting in case of failures of those components. 
- Working in stalled data on queries during the intervals between synchronization data from command source data and queries sources. 
