# FUEL FILTRATION - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Separates carbon dioxide from reduced feedstock mixture and stores both outputs.

## FUNCTIONAL OVERVIEW
* Disables production if the filtration cannot process anymore gas because storage is full or filters are exhausted

## HARDWARE INTERFACE
* d0: QuenchPump (volume pump)

## CONFIGURATION PARAMETERS
| Variable             | Description                             | Setting   |
|----------------------|-----------------------------------------|-----------|
| `MinPressureVolume`  | Filtration activation threshold - kPa*L | `10132.5` |
| `MaxMethanePressure` | Methane storage cutoff - kPa            | `3080.72` |
| `MinFilterQuantity`  | Minimum filter life threshold           | `15`      |

## MAINTENANCE AND TROUBLESHOOTING

### No gas throughput

**STEP 1: Check power**

1.1 Is the `FUEL-PROD` network powered?
* IF NO  - Check system power
* IF YES - Continue to Step 2

**STEP 2: Check pipe settings**

2.1 Is there is at least 10MPa*L gas in the input pipe?
* IF NO  - Continue to Step 2.2
* IF YES - System normal

2.2 Is there at least 3MPa gas in the methane pipe?
* IF NO  - Continue to Step 2.3
* IF YES - System normal, fuel production is disabled to prevent pipe damage from condensation

2.3 Is the sum of all filters < 15?
* IF NO  - Refer to [Fuel Quench System Operations Manual](fuel_quench_operations_manual.md#maintenance-and-troubleshooting)
* IF YES - System normal, fuel production is disabled to prevent pipe damage from condensation