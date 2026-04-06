# PAD RESOLVER - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Given a slot request, determines whether a contact can land at the assigned pad.

# FUNCTIONAL OVERVIEW
* Registers the landing dish reference id
* Checks landing pad availability
* Compares contact characteristics to verify if ship can land at the assigned pad
* Writes the result to the Setting

## HARDWARE INTERFACE
* **d0:** Dish (Reference ID)
* **d1:** Landing Pad
* **d2:** Terminal Index
* **d3:** Terminal Accepts
* **d5:** Contact Slot

## VALIDATION CRITERIA
Each contact type is assigned a bit position. Setting that bit in the Terminal Accepts input indicates the pad supports that contact type. A pad that accepts Utility and Basic contacts has bits 0 and 1 set — a value of 3.

## RESPONSE
| Position | Field              | Data Type |
|----------|--------------------|-----------|
| 0-7      | CONTACT_SLOT_INDEX | INT_8     |
| 8-15     | TERMINAL_INDEX     | BYTE_8    |
| 16-23    | IS_AVAILABLE       | BYTE_8    |
