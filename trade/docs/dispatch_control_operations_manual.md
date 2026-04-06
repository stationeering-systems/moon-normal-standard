# DISPATCH CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Lands a qualified contact

## FUNCTIONAL OVERVIEW
* A contact is qualified when:
  * The signal is locked
  * The trader presents a desirable opportunity 
  * There is a compatible and available landing pad 
  * The trader will land before the signal expires 
* The qualified contact with the highest power ratio and doesn’t exceed the contact threshold is selected to land 
* The terminal assignment is written to Setting

## HARDWARE INTERFACE
* **d0:** Call Dish
* **d3:** Movement Calculator
* **d4:** Power Calculator
* **d5:** Contact Slot

## CONFIGURATION PARAMETERS
| Variable              | Description                                          | Setting              |
|-----------------------|------------------------------------------------------|----------------------|
| `ContactThreshold`    | Maximum power ratio to consider for interrogation    | `1.2`                |
| `MaxContactThreshold` | Power ratio limit for contact feasibility            | `2`                  |
| `ManifestResolver`    | label                                                | `"ManifestResolver"` |
| `PadResolver`         | label                                                | `"PadResolver"`      |
