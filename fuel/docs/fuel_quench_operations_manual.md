# FUEL QUENCH - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE

Rapidly cools hot feedstock mixture to meet target distillation requirements.

## FUNCTIONAL OVERVIEW
* Calculates the amount of energy required to cool feedstock to target temperature
* Accounts for error in enthalpy calculation based on dew pipe conditions
* Accounts for latent heat released during condensation

## HARDWARE INTERFACE
* **d0:** Quench Pipe (pipe analyzer)
* **d1:** Quench Pump (volume pump)
* **d2:** Drain Pump (volume pump)
* **d3:** Dew Pipe (pipe analyzer)

## CONFIGURATION PARAMETERS
| Variable             | Description                          | Setting |
|----------------------|--------------------------------------|---------|
| `TargetTemperature`  | Target bubble temperature K          | 342     |
| `PollutantFuelRatio` | Target pollutant content in fuel mix | 0.03    |
| `kR`                 | Radiator radiation coefficient       | 3.46    |
| `kN`                 | Enthalpy limit factor 2^N            | 2       |
| `V`                  | Cooling pipe volume L                | 20      |

## KNOWN ISSUES
* **Quench radiators may lose heat capacity on world load.**  For pipe networks with a one-tick residency time, this fluctuation is enough to push dew pipe temperatures above the maximum target, stalling production.
  * Identification:
    1. The quench controller `Setting` register displays a value < 0.
    2. Neither quench radiator has a `Radiated` value greater than 20 kJ
  * Fix:
    1. Attach a temporary convection radiator onto the dew pipe.  The quench drain pump will briefly start pumping before stalling.
    2. When the quench pump stalls, detach the convection radiator and the quench pipe radiators.
    3. Reattach all three radiators again. Wait for the pump to restart.
    4. Detach the convection radiator.

## MAINTENANCE AND TROUBLESHOOTING

### No gas throughput

**STEP 1: Check power**

1.1 Is the `FUEL-PROD` network powered?
* IF NO  - Check system power
* IF YES - Continue to Step 1.2

1.2 Is the Dew Pump on?
* IF NO  - Check connections and system settings
* IF YES - Continue to Step 1.3

1.3 Is the Quench Pump on?
* IF NO  - Refer to [Fuel Filtration Operations Manual](fuel_filtration_operations_manual.md#maintenance-and-troubleshooting)
* IF YES - Continue to Step 2

**STEP 2: Check pipe settings**

2.1 Is the quench controller `Setting` > 0?
* IF NO  - Refer to [Known Issues](#known-issues)
* IF YES - Continue to Step 2.2

2.2 Is there adequate gas in the staging pipe?
* IF NO  - Continue to Step 2.3
* IF YES - Further investigation required

2.3 Is the pressure regulator on?
* IF NO  - Continue to Step 2.4
* IF YES - Continue to Step 2.5

2.4 Is the volatiles pipe analyzer on?
* IF NO  - System Normal, volatiles pipe analyzer must be manually turned on
* IF YES - Continue to Step 2.5

2.5 Is there adequate and compatible volatiles gas available?
* IF NO  - System Normal
* IF YES - Further investigation required