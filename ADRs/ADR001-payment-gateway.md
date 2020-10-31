# ADR 004: Use Payment Gateway in self-hosted mode 
There are different versions of the Farmacy Food app (web version, iOS native app, Android native app). 
The app can take orders and give customers flexible yet secure payment options.  
The payment solution should be simple and easy to use, provide scalability, and work on native mobile apps.

## Decision 
In the long run, we will use a commercial payment gateway in self-hosted (integrated) mode.
However, during a transition period, we will use the payment gateway in hosted mode for the Web app. 

## Rationale 
Though a *hosted* payment gateway solution is simpler to roll out, it has some drawbacks:
- in the case of the Web app, the user is directed to a separate web site to complete the payment (the payment gateway 
provider web site). The user experience is not seamless thoughout.  
- in the case of the native apps, the user is directed to a separate app.
- transaction fees tend to be higher than in self-hosted mode.
- the merchant still needs to be PCI DSS compliant. 

With the self-hosted option, we privilege the user experience and bring upon Farmacy Food an increased burden on 
information security. 

## Status
Proposed. 

## Consequences
- Farmacy Food needs to put in place information security measures to make the payment 
handling [PCI DSS compliant](https://en.wikipedia.org/wiki/Payment_Card_Industry_Data_Security_Standard). SSL digital
certificate and other security constraints need to be implemented.
- Farmacy Food apps can have a customized and visually consistent checkout user experience. 
- Payment confirmation can occur in the background  