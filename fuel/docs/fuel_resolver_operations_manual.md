# FUEL MANIFEST RESOLVER - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Given a slot request, determines whether a contact requests fuel to purchase

## FUNCTIONAL OVERVIEW
* Loads the stack instructions to the manifest dish
* Compares contact characteristics to verify if the ship presents a matching trade opportunity
* Writes the result to the Setting

## HARDWARE INTERFACE
* **d0:** Dish
* **d5:** ContactSlot

## CONFIGURATION PARAMETERS
| Variable           | Description                          | Setting |
|--------------------|--------------------------------------|---------|
| `BuyLineItemSize`  | Stack addresses reserved for results | `7`     |


## RESPONSE
| Position | Field              | Data Type |
|----------|--------------------|-----------|
| 0-7      | CONTACT_SLOT_INDEX | INT_8     |
| 8-15     | OPPORTUNITY_STATE  | BYTE_8    |

**OPPORTUNITY_STATE** occupies bits 8-9 and represents one of three values:
* 0 — Not Observing. The resolver is not currently monitoring this contact slot.
* 1 — Observing, No Opportunity. The resolver is monitoring this slot but has not identified a trade opportunity.
* 2 — Has Opportunity. The resolver has identified a trade opportunity for this contact.