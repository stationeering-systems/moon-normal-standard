# THERMAL EXCHANGE CORE - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Pumps waste gases from the **Exchange Capture Line** into the **Thermal Exchange Core** to cool gases to target temperatures and filter impurities.

## FUNCTIONAL OVERVIEW
* Directs heating or cooling of gases via connected devices to maintain target temperature thresholds.
* Commands gas intake into the TEC pipe to maintain target thresholds, or when conditions indicate poor condensation efficiency — based on a calculated condensation ratio derived from gas pressure and temperature.
* Removes unwanted gases through multiple pathways: volatile components are filtered by the TEC-V, while nitrous oxide and pollutant condensates are phase-changed and vented through the passive drain.
* A manual release valve is available to purge the TEC line in the event of volatile contamination or failed condensation.

## TEMPERATURE CONTROL
* **Heating:** Activates heater when gas temperature **falls** below the `MinTemperature`.
* **Cooling:** Activates cooling loop when gas temperature **rises** above `MaxTemperature`.
    * TEC-C monitors cooling activation and flushes the cooling pipe when the Thermal Regulator is disabled.

## HARDWARE INTERFACE
* **Controller Slot (db):** IC10 - TEC Filtration Unit
* **d0:** Pipe Heater (controls heating via attached device)
* **d1:** Thermal Regulator (controls access to the cooling loop)

### PIPE CONNECTIONS
* **Input**: Exchange Capture Line
* **Output**: Volatiles Purge Vent
* **Output2**: PGL Intake and Cooling Loop

## CONFIGURATION PARAMETERS
| Variable            | Description                                       | Setting  |
| ------------------- | ------------------------------------------------- |----------|
| `MaxPressure`       | Maximum Pipe Pressure (kPa)                       | `48636`  |
| `MinPressure`       | Minimum Pipe Pressure (kPa)                       | `6.3`    |
| `MaxTemperature`    | Maximum Pipe Temperature (K)                      | `298.15` |
| `MinTemperature`    | Minimum Pipe Temperature (K)                      | `293.15` |
| `MinPressureVolume` | Minimum Pipe Pressure Volume (kPa*L)              | `30000`  |
| `CondensationRatio` | Condensation Purge Gas Ratio (kPa/K)              | `13.79`  |

## FAILSAFE
* If the TEC pipe's pressure drops to zero, a logic circuit disables the TEC-FS area power controller to prevent additional gas loss.  This requires a **manual reset:**

### Failsafe Reset Procedure:
1. **Confirm** output pressure is `0 kPa`.
2. **Verify** that the manual release valve is closed.
3. **Inspect** and replace any damaged pipes from TEC pipe to the filtration system.
4. **Disable** the logic writer labeled `Failsafe Control`.
5. **Manually enable** the area power controller.
6. **Once pressure stabilizes**, re-enable the `Failsafe Control`.

> If the transformer is **on and receiving power**, but the **filtration unit is not**, it's likely a power distribution issue. Double-check wiring and transformer wattage.

## MAINTENANCE & TROUBLESHOOTING

### TEC Filtration Unit is not pumping

**STEP 1: Check Power**

1.1 Is the filtration unit powered?
* IF NO  - Continue to Step 1.2
* IF YES - Continue to Step 2

1.2 Is the `TEC-FS` power controller on?
* IF NO  - System failsafe engaged.  Refer to [Failsafe Reset Procedure](#failsafe-reset-procedure).
* IF YES - Continue to step 1.3

1.3 Is the `TEC` transformer powered?
* IF NO  - Check ARU system power
* IF YES - Double check wiring and transformer wattage.

**STEP 2: Check TEC "Output Pipe"**

2.1 Is the output pressure * volume >= 30,000 kPa\*L?
* IF NO  -  Continue to Step 3
* IF YES -  System Normal

**STEP 3: Check TEC-V Filtration Unit**

3.1 Are the filters empty?
* IF NO  - Continue to Step 4
* IF YES - Replace filters and retest

**STEP 4: Check ECL "Input Pipe"**

4.1 Is the input pressure >= 6.3 kPa?
* IF NO  - System Normal
* IF YES - Further investigation is required

## NOTES
- Operates continuously while exhaust gases are present.
- Pump activates when the valve is not powered to prevent pipe damage from over-cooling.
    - Pump operates on a backup power system for redundancy.
- The Failsafe will deactivate the TEC-V Filtration unit, Cooling Valve and Pipe Heater.

> For cooling loop control logic see the [TEC Cooler Operations Manual](tec_cooler_operations_manual.md)