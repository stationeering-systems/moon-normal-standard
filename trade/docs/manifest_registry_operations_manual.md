# (1) MANIFEST REGISTRY - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Maintains the list of manifest dishes organized by contact slot index.

## FUNCTIONAL OVERVIEW
* Exposes its reference id on the traffic data network
* Registers dishes used for manifest resolution
* Updates the zenith dish to the signal id of the slot request

## HARDWARE INTERFACE
* **d0:** Zenith Dish
* **d1:** Large Dish
* **d2:** Exotic Dish
* **d5:** Contact Slot

## RESPONSE
| Position | Field              | Data Type |
|----------|--------------------|-----------|
| 0-7      | CONTACT_SLOT_INDEX | INT_8     |
| 8-15     | IS_VISIBLE         | BYTE_8    |

