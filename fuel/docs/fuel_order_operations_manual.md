# FUEL ORDER - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Compares EMA demand with current inventory to determine the purchase amounts of each required commodity.

## FUNCTIONAL OVERVIEW
* Computes the amount of dirty volatiles to purchase based on EMA and flow rate requirements
* Computes the amount of oxygen to purchase EMA
* Computes the amount of pollutant to purchase based on Volatile content

## HARDWARE INTERFACE
* **d0:** EMA
* **d1:** Volatiles (Logic Memory)
* **d2:** Oxygen (Logic Memory)
* **d3:** Pollutant (Logic Memory)

## CONFIGURATION PARAMETERS
| Variable              | Description                                        | Setting           |
|-----------------------|----------------------------------------------------|-------------------|
| `MethaneRatio`        | Ratio of mixture from methane storage              | `0.68`            |
| `OxygenRatio`         | Ratio of mixture from oxygen storage               | `0.32`            |
| `PollutantContentMin` | Minimum pollutant content of the feedstock mixture | ` 0.033815`       |
| `PollutantContentMax` | Maximum pollutant content of the feedstock mixture | `0.1179968`       |
| `Period`              | Replenishment period (ticks)                       | `7200`            |
| `FuelPipe`            | (label)                                            | `"FuelPipe"`      |
| `VolatilesPipe`       | (label)                                            | `"VolatilesPipe"` |
| `MethanePipe`         | (label)                                            | `"MethanePipe"`   |
| `OxygenPipe`          | (label)                                            | `"OxygenPipe"`    |

## PURCHASE FORMULAS
Each formula derives the net purchase quantity for a commodity from the current demand signal and inventory state.  Results are converted into trader request units (1 unit = 100 moles), rounded up, and floored at zero.

### VOLATILES
Derives the dirty volatiles needed to meet one target supply horizon of fuel demand, accounting for fuel already produced, processed methane on hand, and the methane-equivalent content of unprocessed volatiles already in storage.

```
target_moles = EMA * 100
target_moles = target_moles - FuelPipe_moles
target_moles = (target_moles * MethaneRatio - MethanePipe_moles) / MethaneRatio
target_moles = target_moles - (VolatilesPipe_moles * (1 - VolatilesPipe_ratioPollutant))
target_moles = target_moles * (1 + 4 * VolatilesPipe_volume / Period * (1 / VolatilesPipe_volume + 0.01))
result = ceil(target_moles / 100), min 0
```

**Inventory sources:**  
* `FuelPipe_moles`: total moles of finished fuel
* `MethanePipe_moles`: total moles of processed methane (includes pollutant blend)
* `VolatilesPipe_moles`: total moles of unprocessed volatiles in storage
* `VolatilesPipe_ratioPollutant`: current pollutant fraction in the unprocessed tank, used to recover the methane-equivalent volume
* `VolatilesPipe_volume`: total volatiles pipe volume

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
ratio_gap = PollutantContentMin - VolatilesPipe_ratioPollutant
target_moles = (ratio_gap / (1 - PollutantContentMin)) * VolatilesPipe_moles
result = ceil(target_moles / 100)
result_ratio = (VolatilesPipe_ratioPollutant * VolatilesPipe_moles + result * 100) / (VolatilesPipe_moles + result * 100)
if result_ratio > PollutantContentMax:
  result--
result = result, min 0
```

**Inventory sources:**  
* `VolatilesPipe_moles`: total moles of unprocessed volatiles in storage
* `VolatilesPipe_ratioPollutant`: current pollutant fraction of the unprocessed tank