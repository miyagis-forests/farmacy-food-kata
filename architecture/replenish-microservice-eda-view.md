# Replenisher Microservice and EDA View 
The scope is the operations that the Farmacy Food replenisher can perform related to inspecting the stock and replenishing 
the fridges and vendor kiosks. The scope also includes updating in the status of fridges vendor stores. 

This is a microservice architecture. Key patterns used:
- BFF
- Database per Microservice (aka Database per Service)
- CQRS 

![Replenisher microservice and eda view](../images/replenish-microservice-eda-view-primary.png)
![Notation key](../images/notation-key-microservice-views.png)


## Element Catalog 

#### Farmacy Food Android app
- Mobile application created using native language for Android, such as Kotlin or Java.
- It's the application the replenisher uses to enter stock updates into the system, both for fridges and vendor kiosks.  

#### Replenish BFF for Android
- Central access point for calls coming from the Replenisher's Android app.
- Produces inventory events to a Kafka topic for placing or removing meals, and updating stock information.

#### Inventory Command
- Listener to inventory events produced by a replenisher. It updates stock information in the master inventory DB for vendor kiosks and fridges. 

#### Inventory data sync
- Batch program that in a loop reads data from Inventory, Kiosks and Fridges sources in order to synchronize data to Inventory query view. 
It’s important to note that customers (users) need to know what items are available and what points of sale (kiosks and smart fridges)
are operational for purchase and pick up.        

#### Fridge control
- Updates the status of smart fridges (see state machine diagram below) based on different events. 
    - Events coming from the replenisher app indicate meals added/removed from a fridge, and possibly some status information (say, 
    the replenisher found a technical problem to report).
    - Events coming from calling (in a loop) the smart fridge cloud-based system to query the status of fridges.  
- When processing events from the replenisher app, Fridge control will call the third party smart fridge system 
(via a wrapper service) to update stock information based on meals added or removed by the replenisher. 

#### Vendor kiosk control
- Change status of vendor location: open, closed temporarily, business closed
- Working with vendor system, by a wrapper, to update stock information (placing or removing meals)

#### Monitor Fridges
- Batch program that in a loop calls the cloud-based smart fridge management system to get the status of the Farmacy
Food fridges. 
- It makes the calls via a wrapper service. 

#### Monitor Kiosks
- Batch program that in a loop calls the cloud-based vendor kiosk management system to get the status of the vendor kiosks points of sale. 
- It makes the calls via a wrapper service. 

## Behavior
- UML state machine diagram showing the status of a fridge (from a Farmacy Food system perspective).

![State machine of fridges](../images/replenish-microservices-eda-state-machine.png)
 
## Related ADRs 
- [Wrapper pattern](../ADRs/ADR003-wrapper-pattern.md)
- [CQRS pattern](../ADRs/ADR004-cqrs-pattern.md)

## Related Views
- [Order - microservice and EDA view](order-microservice-eda-view.md) 
