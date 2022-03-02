# Quality attribute requirements of the Farmacy Food system

A proper elicitation of quality attribute requirements (aka architecture characteristics, non-functional requirements) 
requires a conversation with various system stakeholders. That conversation would allow: *(i)* specifying these requirements 
in a testable/measurable format; and *(ii)* prioritizing the requirements. 

In this document, we listed a few requirements that we *assumed* would be important for the system.  

## *Interoperability with smart fridge supplier* 
- The cost to adapt the Farmacy Food system to interact with the API provided by a new smart fridge supplier should be 
low (e.g., less than 3 person-days).
- The system must be able to use more than one smart fridge supplier. 

## *Interoperability with vendor POS system* 
- The cost to adapt the Farmacy Food system to interact with the POS system of a given vendor (coffee shop, grocery 
store, etc.) should be low (e.g., less than 3 person-days).
- The system must be able to interact with multiple vendor POS systems. 

## *Scalability (elasticity)*
- The system must quickly and automatically cater to an increasing number of users.
- Meal production in the kitchen may be a bottleneck, but never the software.  :^) 

## *Performance - response time* 
- Customer browsing catalog options, placing orders, and using other app functions should get quick responses (up to 1 second even in peak hours).  

## *Performance - throughput* 
- During peak hours, the system must be able to support a high number of concurrent user sessions (e.g., 100 simultaneous users). 

## *Security*
- User personal data must be protected via encryption in all communication channels. 
- User personal data must be protected via encryption or access control wherever it is stored or manipulated. 
- Payment information (e.g., credit card numbers) must be protected. The Farmacy Food must have basic [PCI DSS compliance](https://en.wikipedia.org/wiki/Payment_Card_Industry_Data_Security_Standard). 

## *App usability* 
- The different versions of the app should provide a user experience that appeals to the target user population. 
- Using UX design techniques, and providing high levels of customization are goals.
- The system should keep the user appraised via notifications (email, app push notification, SMS, whatsApp, or other) of 
steps in fulfilling an order (order placed, payment confirmed, order available for pickup, etc.)
