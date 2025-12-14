# PORT-CAN CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Manages canister fill and evacuation operations across up to six configurable gas lines plus exhaust.

## FUNCTIONAL OVERVIEW
* Activates pressure regulator when canister is connected to a gas supply line
* Activates evacuation volume pump when canister is connected to a gas exhaust line
* Sets the target pressure based on the canister type (1x standard, 2x smart)

## ACCIDENTAL CONTAMINATION
If contamination is detected in the tank storage gas supply lines, first diagnose the source to prevent ongoing contamination. Then, fill canisters from the contaminated line and evacuate them to the exhaust line (ECL) repeatedly until contamination has been purges.  This process wastes gas, but ensures safe operation.

## HARDWARE INTERFACE
* **d0..d5:** Gas Tank Storages

## HARDWARE LABELING
Each Gas Tank Storage requires a matching pressure regulator with an identical label.  The controller uses these paired labels to coordinate fill operations between the regulator (pressure control) and storage (canister connection).

**Example:**
* Gas Tank Storage labeled `PortableOxygen`
* Pressure regulator labeled `PortableOxygen`

## CONFIGURATION PARAMETERS
| Variable           | Description                                               | Setting              |
|--------------------|-----------------------------------------------------------|----------------------|
| `StandardPressure` | Fill pressure for standard canisters (kPa)                | `5182`               |
| `LocalExhaust`     | label                                                     | `"PortableExhaust"`  |

## MAINTENANCE AND TROUBLESHOOTING

### Waste canister not emptying

**STEP 1: Check Power**

1.1 Is the PORT-CAN area power controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.2

1.2 Is the controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.3

1.3 Is the volume pump powered?
* IF NO - Verify system settings and connections
* IF YES - Further investigation required

### Gas canister not filling/filling slowly

**STEP 1: Check Power**

1.1 Is the PORT-CAN area power controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.2

1.2 Is the controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.3

1.3 Is the correct pressure regulator powered?
* IF NO - Verify system settings and connections
* IF YES - Further investigation required