# FUEL DEMAND TRACKER - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Tracks the amount of fuel requested and relays the information to the trade EMA.

## FUNCTIONAL OVERVIEW
* Loads the stack instructions to the landing dish
* Writes the fuel demand quantity to the Setting register
* Writes the activation state to the Demand Reader's On register (this signals the EMA to accumulate the amount)

## HARDWARE INTERFACE
* **d0:** Dish
* **d1:** Reader

## CONFIGURATION PARAMETERS
| Variable           | Description                          | Setting |
|--------------------|--------------------------------------|---------|
| `BuyLineItemSize`  | Stack addresses reserved for results | `7`     |

## KNOWN ISSUES
* **Manifest data may not reflect actual trade availability.** The dish stack can report a buy request that does not appear on the trader's trade menu — for example, a manifest indicating a request for 4 units of fuel while fuel is absent from the trader's available trades entirely.  
This means the demand EMA may accumulate requests that cannot be fulfilled even when the operator is present and the correct commodity is in stock. Treat the demand signal as an estimate of expressed interest rather than a guarantee of executable trades.
* **Gas filtering may not return the correct result in the first stack address.** When filtering the stack for a specific gas, the first matching result is not always the desired one. Reserve multiple stack addresses for results (BuyLineItemSize) to improve the likelihood of finding the correct match.