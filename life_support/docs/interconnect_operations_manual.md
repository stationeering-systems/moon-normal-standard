# INTERCONNECT CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Allows for the safe pressurization of new atmospheric compartments.

## FUNCTIONAL OVERVIEW
* Opens the interconnect valve to allow gas flow from pressurized area to unpressurized compartment
* Closes the interconnect valve if source pressure drops below safety threshold, protecting base atmosphere 
* Closes the interconnect valve and powers down when target pressure is reached in new compartment

## HARDWARE INTERFACE
* **d0:** Pressure kPa
* **d1:** Gas Sensor (unpressurized space)
* **d2:** Digital Valve (interconnect valve)

## CONFIGURATION PARAMETERS
| Variable            | Description                   | Setting    |
|---------------------|-------------------------------|------------|
| `PressureTolerance` | Pipe pressure deviation (kPa) | `5`        |
| `Local`             | label                         | `"Sector"` |

## MAINTENANCE & TROUBLESHOOTING

### Interconnect valve is closed

**STEP 1: Check pressure** 

1.1 Is the destination pressure above 95 kPa?
* IF NO - Continue to STEP 1.2
* IF YES - System normal, pressurization complete

1.2 Is the minimum source pressure above 97 kPa?
* IF NO - Inadequate gas reserves, refer to [MixPress System Operations Manual](mixpress_operations_manual.md)
* IF YES - Verify system settings and connections