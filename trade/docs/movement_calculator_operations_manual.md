# MOVEMENT CALCULATOR - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Estimates the net horizontal distance the call dish must travel that is not offset by vertical movement.

## FUNCTIONAL OVERVIEW
* Loads the position of the call dish and the tracking dish for a slot request
* Predicts combined vertical and horizontal offset from azimuth and elevation speed
* Sign represents the horizontal movement direction of the call dish
* Writes the computed value into the stack by contact slot index
* Writes the index of the most recently updated slot in `Setting`

## HARDWARE INTERFACE
* **d0:** Call Dish
* **d5:** Contact Slot