# HANGAR AIRLOCK CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Handles the pressurization and depressurization of a hangar airlock based on landing pad state.

## FUNCTIONAL OVERVIEW
* Monitors the landing pad mode and sets the airlock's pressurization state accordingly (0,1 = depressurized, 4 = pressurized)
* When the landing pad mode is set to holding (3) the airlock toggles its pressurization state
* State transitions can be overridden by pressing the interrupt button
* Pulses 1 on Setting when transition is complete 

## HARDWARE INTERFACE
* **d0:** Landing Pad Mode (Setting)
* **d1:** Interrupt Button

## CONFIGURATION PARAMETERS
| Variable            | Description                                  | Setting      |
|---------------------|----------------------------------------------|--------------|
| `AirlockPressure`   | Target airlock pressure kPa                  | 101.325      |
| `PressureTolerance` | Rounding error for pressure reading          | 0.01         |
| `SensorQuiesce`     | Seconds to wait to ensure full decompression | 5            |
| `Interior`          | (label)                                      | `"Interior"` |
| `Exterior`          | (label)                                      | `"Exterior"` |
