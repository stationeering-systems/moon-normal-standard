# FUEL ORDER - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Compares EMA demand with current inventory to determine the purchase amounts of each required commodity.

## FUNCTIONAL OVERVIEW
* Computes the amount of dirty volatiles to purchase based on EMA
* Computes the amount of oxygen to purchase EMA
* Computes the amount of pollutant to purchase based on Volatile content

## HARDWARE INTERFACE
* **d0:** EMA
* **d1:** Volatiles (Logic Memory)
* **d2:** Oxygen (Logic Memory)
* **d3:** Pollutant (Logic Memory)

## CONFIGURATION PARAMETERS
| Variable            | Description                                   | Setting           |
|---------------------|-----------------------------------------------|-------------------|
| `MethaneRatio`      | Ratio of mixture from methane storage         | `0.68`            |
| `OxygenRatio`       | Ratio of mixture from oxygen storage          | `0.32`            |
| `PollutantMaxRatio` | Maximum pollutant content of the fuel mixture | `0.03`            |
| `FuelPipe`          | (label)                                       | `"FuelPipe"`      |
| `VolatilesPipe`     | (label)                                       | `"VolatilesPipe"` |
| `MethanePipe`       | (label)                                       | `"MethanePipe"`   |
| `OxygenPipe`        | (label)                                       | `"OxygenPipe"`    |

## PURCHASE FORMULAS
Each formula derives the net purchase quantity for a commodity from the current demand signal and inventory state.  Results are converted into trader request units (1 unit = 100 moles), rounded up, and floored at zero.

### VOLATILES
Derives the dirty volatiles needed to meet one target supply horizon of fuel demand, accounting for fuel already produced, processed methane on hand, and the methane-equivalent content of unprocessed volatiles already in storage.

```
target_moles = EMA * 100
target_moles = target_moles - FuelPipe_moles
target_moles = (target_moles * MethaneRatio - MethanePipe_moles) / MethaneRatio
target_moles = target_moles - (VolatilesPipe_moles * (1 - VolatilesPipe_ratioPollutant))
result = ceil(target_moles / 100), min 0
```

**Inventory sources:**  
* `FuelPipe_moles`: total moles of finished fuel
* `MethanePipe_moles`: total moles of processed methane (includes pollutant blend)
* `VolatilesPipe_moles`: total moles of unprocessed volatiles in storage
* `VolatilesPipe_ratioPollutant`: current pollutant fraction in the unprocessed tank, used to recover the methane-equivalent volume

### OXYGEN
Derives the oxygen needed to meet fuel demand oxygen fraction. **Note:** formula will be revised when CO2 conversion is online.

```
target_moles = (EMA * 100 * OxygenRatio) - OxygenPipe_moles
result = ceil(target_moles / 100), min 0
```

**Inventory sources:**  
* `OxygenPipe_moles`: total moles of oxygen in storage

### POLLUTANT
Derives the pollutant needed to bring the unprocessed volatiles tank to the target blend ratio.  Unlike Volatiles and Oxygen, this formula is purely inventory-driven and does not consume the EMA directly.  
The target blend ratio is expressed as an internal mixture fraction rather than the nominal 3% external ratio.  Adding pollutant changes the total mixture volume, so the target must account for pollutant's own contribution to that volume, while still providing a usable mixture:

```
target_ratio = PollutantMaxRatio / (1 + PollutantMaxRatio) # ~0.0291
ratio_gap = target_ratio - VolatilesPipe_ratioPollutant
target_moles = (ratio_gap / (1 - target_ratio)) * VolatilesPipe_moles
result = ceil(target_moles / 100)
result_ratio = (VoltatilesPipe_ratioPollutant * VolatilesPipe_moles + result * 100) / (VolatilesPipe_moles + result * 100)
if result_ratio > PollutantContentLimit:
  result--
result = result, min 0
```

**Inventory sources:**  
* `VolatilesPipe_moles`: total moles of unprocessed volatiles in storage
* `VolatilesPipe_ratioPollutant`: current pollutant fraction of the unprocessed tank

**Configuration:**  
* `PollutantMaxRatio` = 0.03: target pollutant as a fraction of total fuel volume (external ratio)