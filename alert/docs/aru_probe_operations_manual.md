# (5) ARU PROBE - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors ARU and pipeline conditions to ensure ARU operability

## FUNCTIONAL OVERVIEW
* Monitors filter life
* Monitors pipe and gas conditions against specified thresholds

## CONFIGURATION PARAMETERS
| Variable         | Description                       | Setting         |
|------------------|-----------------------------------|-----------------|
| `MinTemperature` | Minimum pipe temperature K        | `293.15`        |
| `MinPressure`    | Minimum PGL pipe pressure kPa     | `288`           |
| `MaxPressure`    | Maximum ECL,PGL pipe pressure kPa | `38908`         |
| `FilterSlot1`    | label                             | `"FilterSlot1"` |
| `FilterSlot2`    | label                             | `"FilterSlot2"` |
| `ECL`            | label                             | `"ECL"`         |
| `TEC`            | label                             | `"TEC"`         |
| `PGL`            | label                             | `"PGL"`         |

## SENSORS
| Device            | Label       | Purpose                                                   |
|-------------------|-------------|-----------------------------------------------------------|
| Pipe Analyzer     | ECL         | Monitors ECL Pipe conditions                              |
| Pipe Analyzer     | TEC         | Monitors TEC Pipe conditions                              |
| Pipe Analyzer     | PGL         | Monitors each PGL Pipe conditions                         |
| Batch Slot Reader | FilterSlot1 | Monitors Warning Slot Quantity of all filtration devices  |
| Batch Slot Reader | FilterSlot2 | Monitors Critical Slot Quantity of all filtration devices |

## ALERT STATES
| Condition                | Alert            |
|--------------------------|------------------|
| Pipe burst               | 35 (CRITICAL)    |
| (PGL) Low pressure       | 35 (CRITICAL)    |
| Critical filter depleted | 25 (WARN)        |
| (ECL) High pressure      | 25 (WARN)        |
| (PGL) High pressure      | 25 (WARN)        |
| Low temperature          | 25 (WARN)        |
| Warning filter depleted  | 15 (MAINTENANCE) |