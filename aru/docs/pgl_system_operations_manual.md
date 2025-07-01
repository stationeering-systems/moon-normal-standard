# PROCESSED GAS LINE - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Pumps and separates gases from the **Thermal Exchange Core** to the **Processed Gas Line** for storage and recirculation.

## FUNCTIONAL OVERVIEW
* Operates PGL filtration units for Oxygen, Nitrogen, and Carbon Dioxide.
* Evaluates gas temperature and pressure-volume thresholds
* Verifies gas composition meets minimum ratio requirement.
* Activates corresponding PGL unit to transfer gas into its dedicated line.
* Prevents gas movement if temperature or purity conditions are not met.

## HARDWARE INTERFACE
* **Controller Slot (db)**: IC10 - Any PGL unit

## CONFIGURATION PARAMETERS
| Variable               | Description                                       | Setting                  |
| ---------------------- | ------------------------------------------------- | ------------------------ |
| `MaxPressure`          | Maximum Pipe Pressure (kPa)                       | `48636`                  |
| `MaxTemperature`       | Maximum Pipe Temperature (K)                      | `303.15`                 |
| `MinTemperature`       | Minimum Pipe Temperature (K)                      | `293.15`                 |
| `MinPressureVolume`    | Minimum Pipe Pressure Volume (kPa*L)              | `30000`                  |
| `MinRatio`             | Minimum Target Gas Pressure Ratio                 | `0.33`                   |
| `CarbonDioxideGasPipe` | label                                             | `"CarbonDioxideGasPipe"` |
| `NitrogenGasPipe`      | label                                             | `"NitrogenGasPipe"`      |
| `OxygenGasPipe`        | label                                             | `"OxygenGasPipe"`        |

### DEVICE MAPPING
Each gas type must include:
* **Filtration**: Manages the throughput of gases into the PGL pipe.

### PIPE CONNECTIONS
* **Input:** TEC-V Output2 (shared line from the Thermal Exchange Core)
* **Output:** Individual insulated lines routed to:
    * Oxygen storage tank
    * Nitrogen storage tank
    * Carbon Dioxide Storage Tank

## MAINTENANCE & TROUBLESHOOTING

### PGL Filtration Unit is not pumping

**STEP 1: Check Power**

1.1 Is the filtration unit powered?
* IF NO  - Check ARU system power
* IF YES - Continue to Step 2

**STEP 2: Check PGL "Output Pipe"**

2.1 Is the output pressure < 48,636 kPa?
* IF NO  -  System Normal
* IF YES -  Continue to Step 3

**STEP 3: Check PGL Filtration Unit**

3.1 Are the filters empty?
* IF NO  - Continue to Step 4
* IF YES - Replace filters and retest

**STEP 4: Check TEC "Input Pipe"**

4.1 Is the input temperature between 293.15 K (20 C) and 303.15 K (30 C)?
* IF NO  - System Normal
* IF YES - Continue to Step 4.2

4.2 Is the input pressure\*volume >= 10,000 kPa\*L?
* IF NO  - System Normal
* IF YES - Continue to Step 4.3

4.3 Is targeted gas ratio >= 0.33?
* IF NO  - Sytem Normal
* IF YES - Further investigation is required

## NOTES
* Only one IC10 controller is needed to manage all PGL filtration units.
* Each unit must be labeled and piped correctly to avoid cross-contamination.
* Excess or unqualified gases are held in TEC pipes until conditions are met.