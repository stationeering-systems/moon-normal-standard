# (5) VCU PROBE - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors VCU and pipeline conditions to ensure VCU operability

## FUNCTIONAL OVERVIEW
* Monitors pipe integrity
* Monitors filter life
* Monitors quench throughput

## CONFIGURATION PARAMETERS
| Variable                 | Description                           | Setting              |
|--------------------------|---------------------------------------|----------------------|
| `MaxPressure`            | Maximum pipe pressure kPa             | 38908                |
| `MaxPollutantPressure`   | Maximum pollutant pipe pressure kPa   | 3080.72              |
| `LowFilterQuantity`      | Low filter maintenance threshold      | 100                  |
| `CriticalFilterQuantity` | Critical filter maintenance threshold | 15                   |
| `PipeNetworkFault`       | label                                 | `"PipeNetworkFault"` |
| `GasPipe`                | label                                 | `"GasPipe"`          |
| `PollutantPipe`          | label                                 | `"PollutantPipe"`    |
| `FilterSlot`             | label                                 | `"FilterSlot"`       |
| `QuenchSensor`           | label                                 | `"QuenchSensor"`     |

## SENSORS
| Device            | Label            | Purpose                                             |
|-------------------|------------------|-----------------------------------------------------|
| Batch Reader      | PipeNetworkFault | Monitors fuel pipe network for any failures         |
| Pipe Analyzer     | GasPipe          | Monitors pipe integrity for non-condensing mixtures |
| Pipe Analyzer     | PollutantPipe    | Monitors pipe integrity for condensing mixtures     |
| Batch Slot Reader | FilterSlot       | Monitors filter life                                |
| Logic Reader      | QuenchSensor     | Monitors quench pump throughput                     |

## ALERT STATES
| Condition                | Alert            |
|--------------------------|------------------|
| Pipe burst               | 35 (CRITICAL)    |
| Quench stalled           | 25 (WARN)        |
| High Pressure            | 25 (WARN)        |
| Critical filter depleted | 25 (WARN)        |
| Warning filter depleted  | 15 (MAINTENANCE) |