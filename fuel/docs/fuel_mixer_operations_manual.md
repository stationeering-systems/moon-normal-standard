# FUEL MIXER - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Mixes gas from methane and oxygen lines to produce fuel.

## FUNCTIONAL OVERVIEW
* Creates fuel up to a specified molar limit
* Only activates when neither input lines are receiving gas
  * Monitors Filtration.Mode (methane)
  * Monitors On state of terminals' oxygen connector (via logic reader)

## HARDWARE INTERFACE
* **d0:** Limit (logic memory)
* **d1:** Gas Mixer
* **d2:** Filtration
* **d3:** Oxygen Pipe (pipe analyzer)
* **d4:** Fuel Pipe (pipe analyzer)

## CONFIGURATION PARAMETERS
| Variable          | Description                                | Setting             |
|-------------------|--------------------------------------------|---------------------|
| `OxygenRatio`     | Target ratio of oxygen in the fuel mixture | `0.32`              |
| `OxygenConnector` | label                                      | `"OxygenConnector"` |

## MAINTENANCE AND TROUBLESHOOTING

### No fuel in pipe

**STEP 1: Check power**

1.1 Is the `FUEL-PROD` network powered?
* IF NO  - Check system power
* IF YES - Continue to Step 2

**STEP 2: Check inventory**

2.1 Is the fuel limit setting > 0
* IF NO  - Check system wiring and settings
* IF YES - Continue to Step 2.2

2.2 Is there gas in the methane and oxygen pipes?
* IF NO  - Refer to [Fuel Filtration Operations Manual](fuel_filtration_operations_manual.md#maintenance-and-troubleshooting)
* IF YES - Continue to Step 2.3

2.3 Are any of the pads pressurized?
* IF NO  - Further investigation required
* IF YES - System Normal