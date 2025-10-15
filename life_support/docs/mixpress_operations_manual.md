# MIXTURE-PRESSURE CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Regulates sector pressure and atmospheric mixture while maintaining safe exhaust pipe pressures.

## FUNCTIONAL OVERVIEW
* Activates ventilation systems to maintain correct atmospheric pressures and gas ratios.
* Monitors waste pipe pressure to ensure safe levels and activates pumps as needed.

## WASTE MANAGEMENT
* Monitors local exhaust line pressure
* Activates pumps when pressure exceeds safety threshold
* Prevents pipe burst risk near structurally sensitive areas

## INWARD VENTILATION
* Takes precedence over outward ventilation when sector pressure exceeds target or when a correction is required

## GAS SELECTION BEHAVIOR
* **Pressure Corrections:** Opportunistic selection during pressure management cycles.  When sector pressure falls below target, the system cycles through available gas types and activates whichever detects a supply opportunity first.  Selection returns to normal iteration for the next tick, ensuring balanced gas activation over time.
* **Composition Corrections:** Priority selection when gas ratios fall below target thresholds.  The deficient gas type maintains activation priority until composition targets are achieved.  Once the ratio correction is complete, the system returns to standard operational models.

## HARDWARE INTERFACE
* **d0:** Pressure kPa
* **d1:** Zone Size GU
* **d2:** Ratio Carbon Dioxide decimal
* **d3:** Ratio Nitrogen decimal
* **d4:** Ratio Oxygen decimal

## CONFIGURATION PARAMETERS
| Variable             | Description                                  | Setting                 |
|----------------------|----------------------------------------------|-------------------------|
| `SafetyPressure`     | Safety pipe pressure (kPa)                   | `48636`                 |
| `PressureTolerance`  | Pipe pressure deviation (kPa)                | `3`                     |
| `MinDisplacement`    | Minimum gas displacement (kPa)               | `0.3`                   |
| `Delay`              | Delay between atmospheric adjustments (tick) | `2`                     |
| `Precision`          | Decimal precision for value comparisons      | `0.001`                 |
| `Local`              | label                                        | `"Sector"`              |
| `LocalCarbonDioxide` | label                                        | `"SectorCarbonDioxide"` |
| `LocalNitrogen`      | label                                        | `"SectorNitrogen"`      |
| `LocalOxygen`        | label                                        | `"SectorOxygen"`        |

## MAINTENANCE & TROUBLESHOOTING

### Sector atmospheric pressure is high

**STEP 1: Check power**

1.1 Are the inward vents powered?  
_They should be pulsing at 1-second intervals._ 
* IF NO - Continue to STEP 1.2
* IF YES - Continue to STEP 2

1.2 Is the controller/network powered?
* IF NO - System undersized, recalibration needed
* IF YES - Verify system settings and connections

**STEP 2: Check flow rates**

2.1 Are inward vents operating at optimal flow rates?
* IF NO - Continue to STEP 2.2
* IF YES - Check for circulation issues/gas leaks.

2.2 Is exhaust pipe pressure above safety limits?
* IF NO - Further investigation required
* IF YES - Verify pump activation and throughput

**If pressure is dangerously high, manually vent excess pressure through airlock valve**

### Sector atmospheric pressure is low

**STEP 1: Check power**

1.1 Are the outward vents powered?  
_They should be pulsing at 1-second intervals._
* IF NO - Continue to STEP 1.2
* IF YES - Continue to STEP 2

1.2 Is the controller/network powered?
* IF NO - System undersized, recalibration needed
* IF YES - Verify system settings and connections

**STEP 2: Check flow rates**

2.1 Are outward vents operating at optimal flow rates?
* IF NO - Continue to STEP 2.2
* IF YES - Check for circulation issues/gas leaks.

2.2 Is there adequate gas pressure in the pipe (>=471 kPa)?
* IF NO - Continue to STEP 3
* IF YES - Further investigation required

**STEP 3: Check pipe distribution network**

3.1 Is there adequate gas pressure on the main line (>= 471 kPa)?
* IF NO - Continue to STEP 3.2
* IF YES - Ensure that valves are correctly installed and open.

3.2 Are there any pipe ruptures?
* IF NO - Refer to [PGL System Operations Manual](../../aru/docs/pgl_system_operations_manual.md)
* If YES - Further investigation required.

### Zone atmospheric composition is below target

**STEP 1: Check power**

1.1 Are the target outward vents powered?  
_They should be pulsing at max 2-second intervals._
* IF NO - Continue to STEP 1.2
* IF YES - Continue to STEP 2

1.2 Is the controller/network powered?
* IF NO - System undersized, recalibration needed
* IF YES - Verify system settings and connections

**STEP 2: Check flow rates**

2.1 Are target outward vents operating at optimal flow rates?
* IF NO - Continue to STEP 2.2
* IF YES - Check for circulation issues/gas leaks.

2.2 Is there adequate gas pressure in the pipe (>=471 kPa)?
* IF NO - Continue to STEP 3
* IF YES - Further investigation required

**STEP 3: Check pipe distribution network**

3.1 Is there adequate gas pressure on the main line (>= 471 kPa)?
* IF NO - Continue to STEP 3.2
* IF YES - Ensure that valves are correctly installed and open.

3.2 Are there any pipe ruptures?
* IF NO - Refer to [PGL System Operations Manual](../../aru/docs/pgl_system_operations_manual.md)
* If YES - Further investigation required.


## NOTES
- Vents pulse activation rather than run continuously to allow time for equalization.