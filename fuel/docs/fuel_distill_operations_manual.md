# FUEL DISTILL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Removes excess contaminants from the feedstock mixture through condensation.

## FUNCTIONAL OVERVIEW
* Evacuates the blend drain pipe once the target temperature is reached
* Evacuates the bubble pipe once the target composition is reached
* Calculates the amount of gas to pump into the bubble pipe based on the temperature and amount of pollutant

## HARDWARE INTERFACE
* **d0:** DewPipe (pipe analyzer)
* **d1:** DewPump (volume pump)
* **d2:** BubblePipe (pipe analyzer)
* **d3:** BubblePump (volume pump)
* **d4:** DrainPipe (pipe analyzer)
* **d5:** DrainPump (volume pump)

## CONFIGURATION PARAMETERS
| Variable             | Description                                       | Setting     |
|----------------------|---------------------------------------------------|-------------|
| `DrainTemperature`   | Temperature threshold to flush the drain pipe - K | `295`       |
| `TargetTemperature ` | Target bubble temperature - K                     | `342`       |
| `DewOffset`          | Dew pressure offset - kPa                         | `-1579.775` |
| `DewFactor`          | Dew pressure multiplier - kPa/K                   | `17.425`    |
| `Period`             | Max condensation period - tick                    | `55`        |
| `MethaneFuelRatio`   | Target methane content in fuel mix                | `0.65`      |
| `PollutantFuelRatio` | Target pollutant content in the fuel mix          | `0.03`      |
| `VolatileFuelRatio`  | Normalized mixture ratio                          | `0.98`      |

## NOTES
* Dew pump must be manually turned on