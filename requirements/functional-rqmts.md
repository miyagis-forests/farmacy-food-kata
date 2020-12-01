This document contains the functional requirements we elicited for the Farmacy Food system, based on the first Kata session and 
the documents provided to all teams. You will find the _actors_ we identified, and how they interact with the system in major scenarios.

# ***Actors***
- Customer
- Replenisher
- Smart fridge system
- Vendor POS system
- Farmacy Food central kitchen system 


<br>

# ***Customer on the Farmacy Food app <sup>1</sup>***

## Account management 
- Self-register as a Farmacy Food user
- Authenticate using Farmacy Food user ID and password
- Authenticate using Open ID
    - Can be done via an API Gateway (Ambassador, for example)
- Update profile information, including dietary restrictions and health information
- View/update subscription information
- View/update meal order
- View order history

## ***Catalog*** 
- Browse meal options
- Search for meals by ingredient or other criteria
- Search for meal availability per location
    - For the case when the customer wants to pick up the order right away
- See information about a meal: ingredients, nutrition facts, rating, reviews, etc. 
- Browse promotions and coupons 
- Browse subscription plans 
- Find pick-up locations (smart fridges, vendor kiosks, Farmacy Food-run restaurants)
    - Requires integration with maps provider (Google Maps, for example)
    
## ***Orders*** 

- Add, edit quantity, or remove meal to/from shopping cart
- Create, edit, or cancel meal subscription
- Check out: review cart; select pick-up location (with find functionality); enter coupon; enter payment information; review and confirm order (meals, pick-up location, date and time range); display order confirmation code and pick up instructions
- Edit or cancel order 
- Rate a meal that was purchased and picked up
- Add a review for a meal that was purchased and picked up
- Send notification about an order 
    - Examples of notifications: order confirmation; payment confirmation; meal pick up instructions; meal pick up reminders; confirmation that meal was picked up; request for feedback (rate and review meals).
    - May use email, app push notification, SMS, whatsApp, etc.

<br>


# ***Customer at a pick-up location***
## Smart fridge
- Use credit or debit card used for online order to open fridge, and pick up order
- Enter online order confirmation code to open fridge, and pick up order
- Select available meal, pay using credit or debit card to open fridge, and pick up order
## Vendor kiosk
- Present credit or debit card used for online order to cashier, and pick up order
- Present online order confirmation code to cashier, and pick up order
- Pick Farmacy Food meals, possibly alongside other store items, and pay for everything at the cashier

<br>


# ***Replenisher<sup>2</sup> on the Farmacy Food app***

## Smart fridge
- Replenish the fridge (placing or removing meals), and update the stock information
- Confirm stock information after visual inspection
- Change the status of a smart fridge
    - Installed but turned off, operative but offline, operative and online, temporarily out of order, in maintenance by supplier, decommissioned
    - The assumption behind this requirement is that a Farmacy Food representative is co-responsible for inspecting the smart fridges and notifying the smart fridge supplier of any issues
    
## Vendor kiosk
- Replenish the stock at a vendor location (placing or removing meals), and update the stock information
- Confirm stock information after visual inspection
- Change the status of vendor location:
    - Open, closed temporarily, business closed

<br>


# ***Smart Fridge system <sup>3</sup>***
- Our system:
    - Posts or updates a purchase order on the Smart Fridge system: consumer identification<sup>4</sup>; meals and quantities; smart fridge location; date and time range availability
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
        - Done after the replenisher detects an issue or change of status in a fridge
<br>


# ***Vendor POS system***
- Post or update a purchase order: consumer identification; meals and quantities; vendor store location; date and time range availability 
    - Done after a customer places, edits or cancels an order for vendor kiosk pick up
- Query pick up and purchase transactions 
    - Done periodically to find out about picked up orders and ad hoc purchases
    - Can be combined or replaced with a push notification mechanism, if the vendor POS system has that ability
<br>


# ***Farmacy Food central kitchen system***
- Post meal orders
- Post inventory levels for smart fridges
- Post inventory levels for vendor POS

<br>


### Notes
<p><sup>1</sup> Native mobile app or web app.</p>
<p><sup>2</sup> Farmacy Food representative responsible for replenishing the stock of meals in smart fridges and vendor kiosks.</p>
<p><sup>3</sup> Operations correspond to API endpoints that we expect to see in the Smart Fridge cloud-based system.</p>
<p><sup>4</sup> Credit or debit card, or order confirmation code to be presented at the smart fridge for pick up.</p>
