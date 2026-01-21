# (6) GRID PROBE - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors the health of the power grid

## FUNCTIONAL OVERVIEW
* Monitors battery life
* Monitors instantaneous power levels to ensure that wattage doesn't exceed cable limits

## CONFIGURATION PARAMETERS
| Variable           | Description                        | Setting |
|--------------------|------------------------------------|---------|
| `LowCapacity`      | Minimum power usage ratio          | `1.1`   |
| `CriticalCapacity` | Critical minimum power usage ratio | `1`     |
| `HighWattage`      | High watermark for cable wattage   | `80000` |
| `Alpha`            | Actual Power (EMA) learning rate   | `3600`  |

## SENSORS
| Device            | Label               | Purpose                             |
|-------------------|---------------------|-------------------------------------|
| Cable Analyzer    | <n/a>               | Monitors regional cable network     |
| Logic Reader      | PotentialPowerMeter | Mirrors region controller `Setting` |

## ALERT STATES
| Condition                           | Alert         |
|-------------------------------------|---------------|
| Load Shedding                       | 36 (CRITICAL) |
| Loads approaching generation limits | 26 (WARN)     |
| Loads approaching cable limits      | 26 (WARN)     |
