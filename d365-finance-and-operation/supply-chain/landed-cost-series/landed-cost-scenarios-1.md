---
description: '#Landed Cost, #BusinessCase, #D365FnO, #SCM'
---

# Landed Cost Scenarios 1

**Scenario:** We have one Item “P-0001” which we are purchasing from a vendor “Acme Office Supplies”, The item purchase price is “2000$” and Quantity = 1

Now this product is transported by a shipping(freight) vendor “Vendor A” - during transportation, the Item has been charged different costs:

* Freight fee
* Insurance fee
* Fuel fee
* Local Transportation fee

So, now at the time of purchase order creation, we know the estimated cost for each of these:

* Freight is 200$ / Quantity => Freight fee = 200$ x 1 = **200$**
* Insurance, 10% of Item Purchase price => Insurance fee =  10% x 2000$ = **200$**
* Fuel is 1$ / measurement => so let’s say it is 60kg, then Fuel fee = 11$ x 50Kg = **60$**
* Local Transportation is 20 % of "Freight cost" => Local Transport fee = 20% x 200$ = **40$**

Therefore:&#x20;

* Total Estimated cost for Item "P-0001" = 200$ + 200$ +60$ + 40$ = **500$**
* Total Item landed cost for Item "P-0001" = 2000$ +500$ = **2500$**

However, the shipper sends an actual billing as **600$** instead **500$** as before.

So, the final Landed Cost of Item must be recalculated = 2000$ + 600$ = **2600$**. Then, the system should post the adjustment transaction as **100$** based on the Landed Cost Estimation.

***

## **BSD 1: Actual Freight bill received after Item is received and invoiced.**

* Item Cost at the time of Purchase order Invoice: 2000$ + 500$ = 2500$ Estimated cost
* Adjustment due to Actual freight Invoice = 100$ USD

<br>
