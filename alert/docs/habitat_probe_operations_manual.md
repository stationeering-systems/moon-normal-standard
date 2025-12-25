# (7) HABITAT PROBE - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors environmental conditions to ensure proper climate control.

## FUNCTIONAL OVERVIEW
* Monitors thermal usage (if available)
* Monitors gas sensor readings

## CONFIGURATION PARAMETERS
| Variable                | Description                     | Setting          |
|-------------------------|---------------------------------|------------------|
| `MaxThermal`            | Max thermal utilization         | `0.5`            |
| `MinTemperature`        | Minimum temperature threshold K | `293.15`         |
| `MaxTemperature`        | Maximum temperature threshold K | `303.15`         |
| `MinPressure`           | Minimum pressure threshold kPa  | `90`             |
| `MaxPressure`           | Maximum pressure threshold kPa  | `101.325`        |
| `MinRatioCarbonDioxide` | Minimum carbon dioxide ratio    | `0.01`           |
| `MinRatioNitrogen`      | Minimum nitrogen ratio          | `0.76`           |
| `MinRatioOxygen`        | Minimum oxygen ratio            | `0.19`           |
| `ThermalMeter`          | label                           | `"ThermalMeter"` |

## ALERT STATES
| Condition          | Alert         |
|--------------------|---------------|
| Fire               | 37 (CRITICAL) |
| Low CO2            | 37 (CRITICAL) |
| Low N2             | 37 (CRITICAL) |
| Low O2             | 37 (CRITICAL) |
| Low Pressure       | 37 (CRITICAL) |
| High Pressure      | 37 (CRITICAL) |
| Low Temperature    | 37 (CRITICAL) |
| High Temperature   | 37 (CRITICAL) |
| High Thermal Usage | 27 (WARN)     |