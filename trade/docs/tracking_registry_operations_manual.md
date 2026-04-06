# (0) TRACKING REGISTRY - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Maintains the list of tracking dishes organized by contact slot index.

## FUNCTIONAL OVERVIEW
* Exposes its reference id on the traffic data network
* Registers dishes used for contact tracking

## HARDWARE INTERFACE
* **d0:** Utility Dish
* **d1:** Basic Dish
* **d2:** Medium Dish
* **d3:** Large Dish
* **d4:** Exotic Dish
* **d5:** Contact Slot

## RESPONSE
| Position | Field              | Data Type |
|----------|--------------------|-----------|
| 0-7      | CONTACT_SLOT_INDEX | INT_8     |
| 8-15     | IS_LOCKED          | BYTE_8    |

## CONFIGURATION PARAMETERS
| Variable               | Description                    | Setting  |
|------------------------|--------------------------------|----------|
| `TargetSignalStrength` | Maximum locked Signal Strength | `2`      |
