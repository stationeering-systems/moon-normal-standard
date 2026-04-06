# (2) TRADE PROBE - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors the spaceport to inform the operator when new traders have arrived

## FUNCTIONAL OVERVIEW
* Monitors landing pad state

## CONFIGURATION PARAMETERS
| Variable      | Description                             | Setting         |
|---------------|-----------------------------------------|-----------------|
| `Occupied`    | Minimum status for a pad to be occupied | `2`             |
| `LandingPad`  | label                                   | `"LandingPad"`  |

## SENSORS
| Device       | Label      | Purpose                                        |
|--------------|------------|------------------------------------------------|
| Logic Reader | LandingPad | Returns the occupancy state of the landing pad |

## ALERT STATES
| Condition      | Alert            |
|----------------|------------------|
| No pad vacancy | 22 (WARN)        |
| Pad occupied   | 12 (MAINTENANCE) |