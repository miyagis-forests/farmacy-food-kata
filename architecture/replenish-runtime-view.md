# Replenish Microservice View 
The scope is the operations that the replenisher can perform related to replenishing the fridges and vendor kiosk stocks, which includes commission of fridges and all operations involving the fridge’s and vendor’s stocks. 

This is a microservice architecture. Key patterns used:
- BFF
- Database per Microservice (aka Database per Service)
- CQRS 

![Replenish runtime view](../images/replenish-runtime-view-primary.png?raw=true)

## Element Catalog 

#### Farmacy Food Android app
- Mobile application created using native language for Android, such Kotlin or Java.
- Application that replenisher use for replenishing stocks on fridges and vendor kiosks.  

#### Replenish BFF for Android
- Central access point for calls coming from the Android app.
- Produce inventory events for Kafka topic for placing or removing meals, and update the stock information

#### Inventory Command
- Listener to inventory events produced by a replenisher in order to update data in inventory  for vendor kiosks and fridges replenishment. 

#### Fridge control
- Change status of fridges: installed but turned off, operative but offline, operative and online, temporarily out of order, in maintenance by supplier, decommissioned
- Working with third part smart fridges systems, by a wrapper, to update stock information (placing or removing meals)

#### Vendor kiosk control
- Change status of vendor location: open, closed temporarily, business closed
- Working with vendor system, by a wrapper, to update stock information (placing or removing meals)

## Behavior
- N/A.
 
## Related ADRs 
- [BFF pattern](../ADRs/ADR002-bff-pattern.md)
- [Wrapper pattern](../ADRs/ADR003-wrapper-pattern.md)
- [CQRS pattern](../ADRs/ADR004-cqrs-pattern.md)

## Related Views
- TO-DO: link to order view 
