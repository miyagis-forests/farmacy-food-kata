# DDD Context Map

<!-- Short description of the scope and nature of this architecture view. --> 

The following architecture view is a [DDD Context Map](https://learning.oreilly.com/library/view/patterns-principles-and/9781118714706/c07.xhtml). 
It shows how the Farmacy Food system is broken up into bounded contexts (BCs) and how they interact with each other. 

![DDD Context Map](../images/ddd-context-map.png)

![DDD Context Map](../images/ddd-context-map-key.png)


_Subdomains_ reflect and divide the areas of business that are of importance to our system. _Bounded Contexts_
(BC) establish the scope of validity of each of the models in our solution. They make
it clear where every context begins and ends. Business strategy, team dynamics and other technical
aspects are relevant in the design of these boundaries.

Subdomains exist in the problem space and BCs in the solution space. The ideal model
seeks to match these two views, designing BCs that map into exactly one subdomain. Therefore,
in our map, the subdomains under control of our application are each defined exactly as one BC. 

Our model defines ***Inventory*** and ***Order*** as core bounded contexts.
The decision of which BCs are core demands strategic vision. This must take place under
the guidance of _domain experts_. Our proposal chose these two BCs as we envision Farmacy Food's
main business challenge is of a logistics nature.

## Element Catalog 

#### Bounded Contexts and Subdomains

- The BCs can be seen as the logical grouping of the microservices and components portrayed in other views.
As stated, the BCs in our map also depict subdomains.

    ![Bounded context closer look](../images/ddd-context-map-bc-inventory-close.png)

- We designated two BCs as **_core_** (Inventory, Order) and one as **_generic_** (Customer Notification). The
 remaining are classified as **_supporting_** BCs.

- The identified BCs are:
    - **Meal Catalog**
        - Maintains which meals may be available, including their information, such as ingredients, nutrition facts and more.
    - **Inventory** (core)
        - Controls what is currently available -- and where.
    - **_User_**
        - Mainly handles the customer information, such as profile and dietary/health information.
    - **_Review_**
        - Meals reviews and ratings; surveys.
    - **_Order_** (core)
        - Processes orders, keeping track of the global status of all transactions.
    - **_Cart_**
        - Handles the checkout process for single purchases.
    - **_Subscription_**
        - Available and ongoing subscription plans.
    - **_Payment_**
        - Processes the payment for single and subscription-originated purchases.
    - **_Promotion_**
        - Promotions and coupons.
    - **_Location_**
        - Geographical location of the elements relevant to the business.
    - **_Replenish_**
        - Updates the status of smart fridges/vendor kiosks.
    - **_Customer Notification_** (generic)
        - Notifies the customer of updates on their orders.

#### Subdomain

- In our map, only external systems form subdomains that are not also BCs.

    ![Subdomain closer look](../images/ddd-context-map-subdomain.png)

- The cataloged subdomains are:
    - **_Payment Gateway_**
        - External partner that will handle the specifics of payment from the customers.
    - **_Smartfridge_**
        - Cloud management system for Smartfridges.      
    - **_Vendor Kiosk_**
        - Cloud management system for Vendor Kiosks.
    - **_Central Kitchen_**
        - Farmacy Food's ghost kitchen system.
    - **_Geolocation_**
        - Maps and GPS services.
    - **_Identity_**
        - Third-party mechanism for access control, such as OAuth. 
    - **_eDietitian_**
        - Expert system that would generate meals recommendations based on user preferences, health info, and history.


#### Partnership (BC Relationship)
![Partnership BC Relationship closer look](../images/ddd-context-map-relationship-conformist.png)
- TODO GENERATE IMAGE
- A *Partnership* between two BCs indicates that the teams that own such BCs intend
to work closely. In this dynamic, the (likely common) goals of both teams are fulfilled without any kind of priority of one team over the other.
- Given Farmacy Food is a startup, we understand it'll most likely have only one development team. With this in mind, we identified most the
relationships between the designed BCs as partnerships.

#### Conformist (BC Relationship)
![Conformist BC Relationship closer look](../images/ddd-context-map-relationship-conformist.png)
- The Conformist relationship between two bounded contexts (or subdomains) indicates that the _upstream_ (**`U`**) end's
model is accepted/absorbed without translation by the _downstream_ (**`D`**) counterpart.
- In our model, this relationship is used in three scenarios. The integration with the _Identity_
subdomain, mostly because the solutions in this subdomain, e.g. OAuth, are typically widely known and accepted.
The _eDietitian_ subdomain is expected to require some information to generate their decisions and it our system should provide that data as needed. Lastly, given the *Customer Notification* BC is expected
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
