# DDD Context Map

<!-- Short description of the scope and nature of this architecture view. --> 

The following architecture view is a [DDD Context Map](https://learning.oreilly.com/library/view/patterns-principles-and/9781118714706/c07.xhtml). 
It shows how the Farmacy Food system is broken up into bounded contexts (BCs) and how they interact with each other. 

![DDD Context Map](../images/ddd-context-map.png)

![DDD Context Map](../images/ddd-context-map-key.png)


Subdomains reflect and divide the areas of business that have any influence on our system.

Bounded contexts mark the reach of each one of models we use in our solution. They make
clear where each context begins and end. Business strategy, team dynamics and other technical
aspects are relevant in the design of these boundaries.

As subdomains exist in the problem space and BCs in the solution space, the ideal design
seeks to model BCs that map into exactly one subdomain. Therefore, in our map, the subdomains
under control of our application are defined each exactly as one BC. 

As the map shows, our model specifies ***Inventory*** and ***Order** as core bounded contexts.
the establishment of these key BCs demand strategic vision. This typically takes place under
the influence of Domain Experts. Our proposal chose these two BCs as we envision Farmacy Food's
main business challeng is of a logistics nature.

## Element Catalog 


#### Bounded Contexts and Subdomains

![Bounded context closer look](../images/ddd-context-map-bc-inventory-close.png)

The BCs can be seen as the logical grouping of the microservices and components portrayed in other views.
As stated, the BCs in our map also depict subdomains.

We designated two BCs as **_core_** (Inventory, Order) and one as **_generic_** (Customer Notification). The
 remaining are classified as **_supporting_** BCs.

- The identified BCs are:
    - **Meal Catalog**
        - What meals may be available, including ingredients, nutrition facts and other data
    - **Inventory** (core)
        - Controls what is currently available -- and where.
    - **_User_**
        - Mainly handles the customer information, such as profile and dietary/health information.
    - **_Review_**
        - Meals reviews and ratings; Surveys
    - **_Order_** (core)
        - Processes orders, keeping track of the global status of all transactions
    - **_Cart_**
        - Handles the checkout process for single purchases
    - **_Subscription_**
        - Available and ongoing subscription plans
    - **_Payment_**
        - Processes the payment for single and subscription-based purchases
    - **_Promotion_**
        - Promotions and coupons
    - **_Location_**
        - Geographical location of the elements relevant to the business
    - **_Replenish_**
        - Updates the status of smart fridges/vendor kiosks
    - **_Customer Notification_** (generic)
        - Notifies the customer of updates on their orders 

#### Subdomain

In our map, subdomains that are not BCs include only external systems.

![Subdomain closer look](../images/ddd-context-map-subdomain.png)

- The cataloged subdomains are:
    - Payment Gateway
        - External partner that will handle the specifics of payment from the customers
    - Smartfridge
        <!-- - Our system:
            - Posts or updates a purchase order on the Smart Fridge system: consumer identification; meals and quantities; smart fridge location; date and time range availability
                - Done after a customer places, edits or cancels an order for smart fridge pick up
            - Query pick up and purchase transactions 
                - Done periodically to find out about picked up orders and ad hoc purchases
                - Can be combined or replaced with a push notification mechanism, if the smart fridge system has that ability
            - Query inventory levels of one or more fridges
                - Done when the customer is searching for meal availability per location
            - Update fridge inventory 
                - Done after the replenisher replenishes a fridge or confirms stock after visual inspection
            - Query fridge status
            - Update fridge status
                - Done after the replenisher detects an issue or change of status in a fridge -->
        
    - Vendor Kiosk (Subdomain)
        <!-- - Post or update a purchase order: consumer identification; meals and quantities; vendor store location; date and time range availability 
            - Done after a customer places, edits or cancels an order for vendor kiosk pick up
        - Query pick up and purchase transactions 
            - Done periodically to find out about picked up orders and ad hoc purchases
            - Can be combined or replaced with a push notification mechanism, if the vendor POS system has that ability -->
        
    - Central Kitchen
        - Farmacy Food's ghost kitchen system
    - Geolocation (Subdomain)
    - Identity (Subdomain)
    - eDietitian (Subdomain)


#### Partnership (BC Relationship)
![Partnership BC Relationship closer look](../images/ddd-context-map-relationship-conformist.png)
- Given it is a startup with most likely one development team, we specified the
relationships as *Partnership*. Other kinds of relationships may be possible, depending on the dynamics.

#### Conformist (BC Relationship)
![Conformist BC Relationship closer look](../images/ddd-context-map-relationship-conformist.png)
- The Conformist relationship between two bounded contexts (or subdomains) indicates that the _upstream_ (**`U`**) end's
model is accepted/absorbed/taken without modification by the _downstream_ (**`D`**) counterpart.
- In our model, this relationship is used in three scenarios. The integration with the "Identity"
subdomain, mostly because the conventions in this subdomain, e.g. Auth0, are typically widely known and accepted.
The eDietitian subdomain is expected to require some information to take their decisions and it would be
natural our system provides that data as needed. Lastly, given the *Customer Notification* BC is expected
to be generic, some off-the-shelf tool would likely have means of integrating with our BCs with minimized effort.

#### Anticorruption Layer - ACL (BC Relationship)
![ACL Relationship closer look](../images/ddd-context-map-relationship-acl.png)
- An anticorruption layer is used to translate the _upstream_ (**`U`**) model into the ubiquitous language
of the _downstream_ (**`D`**) model. Its goal is to prevent the external model from mudding the BC's implementation.    

#### Types of Integrations Mechanisms between BCs

Our context map mainly shows relationships between the BCs. To make it more complete,
we have also specified in the diagram the technical mechanisms used to integrate each subdomain.

- **Via REST API**
    
    ![BC integration Via REST API closer look](../images/ddd-context-map-bc-via-rest-api.png)
    - This label shows that two BCs are mainly integrated via REST API calls.
- **Via Events**

    ![BC integration Via Events closer look](../images/ddd-context-map-bc-via-events.png)
    - Denotes BCs integrated via Domain Events, typically in a publish-subscribe fashion.

- **Via Data Replication**
    
    ![BC integration Via Data Replication closer look](../images/ddd-context-map-bc-via-data-replication.png)
    - There are a few cases there the integration is achieved via Data Replication, usually managed
    by a batch process.

## Behavior
- N/A.
 
## Related ADRs 
- [Microservice style](../ADRs/ADR001-microservice-style.md)
- [Wrapper pattern](../ADRs/ADR004-wrapper-pattern.md)
- [Payment gateway](../ADRs/ADR002-payment-gateway.md)

<!--
- [AWS as the cloud provider](../ADRs/ADR006-aws-as-cloud-provider.md)
- [BFF pattern](../ADRs/ADR002-bff-pattern.md)cu
- [CQRS pattern](../ADRs/ADR005-cqrs-pattern.md)

-->

## Related Views
- [Context Diagram](context-diagram.md)
- [Hexagonal reference architeture view](hexagonal-reference-architecture.md)
- [User Account Management - microservice view](user-account-mgmt-microservice-view.md)
- [Catalog - microservice view](catalog-microservice-view.md)
- [Order - microservice and EDA view](order-microservice-eda-view.md)
- [Customer at Pick-up Location Microservice and EDA View](customer-pickup-microservice-eda-view.md)
- [Replenisher - microservice and EDA view](replenish-microservice-eda-view.md)

<!--
- [AWS Deployment view](aws-deployment-view.md)
--> 
