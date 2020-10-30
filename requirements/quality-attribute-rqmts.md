# Quality attribute requirements of the Farmacy Food system

A proper elicitation of quality attribute requirements (aka non-functional requirements) requires a conversation with 
various system stakeholders. 
In this document, we listed a few requirements that we assumed would be in place. 

## *Interoperability with smart fridge supplier* 
- The cost to adapt the Farmacy Food system to interact with the API provided by a new smart fridge supplier shall be 
low (ex.: less than 3 person-days).
- The system shall be able to use more than one smart fridge supplier. 

## *Interoperability with vendor POS system* 
- The cost to adapt the Farmacy Food system to interact with the POS system of a given vendor (coffee shop, grocery 
store, etc.) shall be low (ex.: less than 3 person-days)
- The system shall be able to interact with multiple vendor POS systems. 

## *Scalability (elasticity)*
- The system shall quickly and automatically cater to an increasing number of users.
- Meal production in the kitchen may be a bottleneck, but never the software.  :^) 

## *Performance - response time* 
- Customer browsing catalog options, placing orders, and using other app functions should get quick responses (up to 1 second even in peak hours).  

## *Performance - throughput* 
- During peak hours, the system shall be able to have a high number of concurrent user sessions (ex.: 100 simultaneous users). 

## *Security*
- User personal data shall be protected via encryption in all communication channels. 
- User personal data shall be protected via encryption or access control wherever it is stored or manipulated. 
- Payment information (ex: credit card numbers) shall be protected. The Farmacy Food shall have basic [PCI DSS compliance](https://en.wikipedia.org/wiki/Payment_Card_Industry_Data_Security_Standard). 

## *App usability* 
- The different versions of the app shall provide a user experience that appeals to the target user population. 
- Using Ux design techniques, and providing high levels of customization are goals.
- The system shall keep the user appraised via notifications (email, app push notification, SMS, whatsApp, or other) of 
steps in fulfilling an order (order placed, payment confirmed, order available for pick up, etc.)

