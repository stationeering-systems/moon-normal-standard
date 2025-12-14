# PORT-SUIT CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors connected Suit Storages and activates them when a suit is detected that is in need of a top-off.

## FUNCTIONAL OVERVIEW
* Activates suit storage unit when connected suit requires battery charging, waste tank evacuation, and/or breathing and propellant top-off.
* Only activates one suit storage at a time to reduce instantaneous power spikes caused from charging batteries.
* Monitors exhaust pipe pressure to ensure safe levels and activates pumps as needed.

## WASTE MANAGEMENT
* Monitors local exhaust line pressure
* Activates pumps when pressure exceeds safety threshold
* Prevents pipe burst risk near structurally sensitive areas

## ACCIDENTAL CONTAMINATION
If contamination is detected in the suit storage gas supply lines, first diagnose the source to prevent ongoing contamination.  Then select the appropriate remediation approach based on contamination type and affected system.

### O2/N2/CO2 Cross-Contamination

**Breathing line:** Accept the contamination and rely on the suit's internal filtration to scrub the contaminant into the waste tank during normal operation.  The waste evacuation system will remove it during the next recharge cycle.

**Propellant line:** Any gas type functions as propellant.  Evaluate whether accepting the contamination loss is operationally feasible, or proceed with active cleanup if pure N2 is required.

### Active Cleanup

Contamination with hazardous gases or unusable mixes requires active cleanup to prevent combustion risk or death.  Fill canisters from the contaminated line and evacuate them to the exhaust line (ECL) repeatedly until contamination has been purged.  This process wastes gas, but ensures safe operation.

## HARDWARE INTERFACE
* **d0..d5:** Suit Storages

## CONFIGURATION PARAMETERS
| Variable          | Description                                               | Setting              |
|-------------------|-----------------------------------------------------------|----------------------|
| `SafetyPressure`  | Safety pipe pressure (kPa)                                | `48636`              |
| `MaxChargeRatio`  | Maximum charge ratio to account for system rounding error | `0.995`              |
| `LocalPropellant` | label                                                     | `"PortableNitrogen"` |
| `LocalBreathing`  | label                                                     | `"PortableOxygen"`   |
| `LocalExhaust`    | label                                                     | `"PortableExhaust"`  |

## MAINTENANCE AND TROUBLESHOOTING

### Suit battery not charging/charging slowly

**STEP 1: Check Power**

1.1 Is the PORT-SUIT area power controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.2

1.2 Is the controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.3

1.3 Is the storage unit powered?
* IF NO - Continue to STEP 1.4
* IF YES - Confirm that adequate power is available

1.4 Are any of the other device inputs powered?  
_Check the input pins to identify exactly which devices are configured_ 
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.5

1.5 Is the connected device fully charged?
* IF NO - System normal
* IF YES - Further investigation required

### Suit waste tank not emptying

**STEP 1: Check Power**

1.1 Is the PORT-SUIT area power controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.2

1.2 Is the controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.3

1.3 Is the storage unit powered?
* IF NO - Continue to STEP 1.4
* IF YES - Further investigation required

1.4 Are any of the other device inputs powered?  
_Check the input pins to identify exactly which devices are configured_
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.5

1.5 Is the connected device empty or fully charged?
* IF NO - System normal, wait for other devices to finish charging 
* IF YES - Further investigation required

### Breathing and/or propellant tanks not filling/filling slowly

**STEP 1: Check Power**

1.1 Is the PORT-SUIT area power controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.2

1.2 Is the controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.3

1.3 Is the storage unit powered?
* IF NO - Continue to STEP 1.4
* IF YES - Continue to STEP 1.6

1.4 Are any of the other device inputs powered?  
_Check the input pins to identify exactly which devices are configured_
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.5

1.5 Is the connected device empty or fully charged?
* IF NO - System normal, wait for other devices to finish charging
* IF YES - Further investigation required

1.6 Is the pressure regulator activated for the gas type?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 2

**STEP 2: Check Pressure**

2.1 Is the pressure regulator set to correct target?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 2.2

2.2 Is there adequate gas pressure on the main line?
* IF NO - Further investigation required
* IF YES - Verify system settings and connections

### Breathing and/or propellant tanks are overfilling

**STEP 1: Check Pressure**

1.1 Is the pressure regulator set to correct target?
* IF NO - Verify system settings and connections
* IF YES - Further investigation required