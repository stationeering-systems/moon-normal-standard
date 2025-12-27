# HAVEN - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors atmospheric conditions to determine PPE requirements for safe entry.

## FUNCTIONAL OVERVIEW
* Compares gas sensor readings against specified thresholds

## CONFIGURATION PARAMETERS
| Variable                  | Description                                           | Setting  |
|---------------------------|-------------------------------------------------------|----------|
| `ContaminantSuitMin`      | Minimum contaminant threshold for required mask entry | `0.01`   |
| `ContaminantSuitCountMin` | Minimum contaminant types for required suit entry     | `3`      |
| `PressureSuitMax`         | Maximum room pressure for supported suit entry kPa    | `450`    |
| `PressureSuitMin`         | Minimum room pressure for required suit entry         | `160`    |
| `PressureAirMin`          | Minimum partial air pressure for safe entry           | `16`     |
| `TemperatureSuitMax`      | Maximum room temperature for supported suit entry K   | `393.15` |
| `TemperatureSuitMin`      | Minimum room temperature for required suit entry      | `313.15` |
| `TemperatureAirMin`       | Minimum room temperature for safe entry               | `273.15` |

## ENVIRONMENT STATES
| Condition                                                                         | State      |
|-----------------------------------------------------------------------------------|------------|
| Pressure >= PressureSuitMax                                                       | 3 (XTREME) |
| Temperature >= TemperatureSuitMax                                                 | 3 (XTREME) |
| Pressure >= PressureSuitMin                                                       | 2 (HAZARD) |
| O2 Partial Pressure <= PressureAirMin                                             | 2 (HAZARD) |
| Temperature >= TemperatureSuitMin                                                 | 2 (HAZARD) |
| Temperature <= TemperatureAirMin                                                  | 2 (HAZARD) |
| ContaminantRatio >= ContaminantSuitMin & ContaminantCount >= ContaminantSuitCount | 2 (HAZARD) |
| Fire                                                                              | 1 (ADVISE) |
| ContaminantRatio >= ContaminantSuitMin                                            | 1 (ADVISE) |
| No gas sensors detected                                                           | -1 (WORLD) |
