# POWER CALCULATOR - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Computes the power ratio used to interrogate contacts and evaluates the risk of contact expiration during interrogation.

## FUNCTIONAL OVERVIEW
* Determines contact viability by weighing against available energy, movement time, contact age, and weather conditions
* Result ≤ 1 is guaranteed, Result ≥ 2 is infeasible, and between 1 and 2 is uncertain
* Writes the computed value into the stack by contact slot index
* Writes the index of the most recently updated slot in `Setting`

## HARDWARE INTERFACE
* **d0:** Call Dish
* **d1:** Battery
* **d2:** Weather Station
* **d3:** Movement Calculator
* **d5:** Contact Slot

# MAINTENANCE & TROUBLESHOOTING

### Fixed -1 Response Code

**STEP 1: Check network state**

1.1 Is the track registry available?
* IF NO  - Check power and network connections
* IF YES - Continue to Step 1.2

1.2 Is the track dish registered?
* IF NO  - Check track registry device settings
* IF YES - Continue to Step 1.3

1.3 Is the manifest registry available?
* IF NO  - Check power and network connections
* IF YES - Continue to Step 1.4

1.4 Is the manifest dish registered?
* IF NO  - Check manifest registry device settings
* IF YES - Continue to Step 1.5

1.5 Has the signal been resolved?
* IF NO  - System Normal, signal resolution required
* IF YES - Further investigation required