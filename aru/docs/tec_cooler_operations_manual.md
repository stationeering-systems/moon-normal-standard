# THERMAL EXCHANGE COOLER - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Flushes the cooling loop when the Thermal Regulator is deactivated to prevent condensation in the thermal exchange system.

## FUNCTIONAL OVERVIEW
* Monitors the **Thermal Regulator** valve state.
* When the regulator is **disabled**, flushes any remaining gas in the pipe.

## HARDWARE INTERFACE
* **Controller Slot (db):** IC10 - TEC-C
* **d0:** Thermal Regulator (controls access to the cooling loop)

### PIPE CONNECTIONS
**Input:** TEC-V Output2
**Output:** Unused
**Output2:** TEC-V Output2

## POWER DOMAIN
* Runs on **ARU-CRT (Red)** power, ensuring evacuation remains available during transformer loss.

## NOTES
* Designed to **fail safe**: if controller is offline, cooling gases may remain trapped, increasing condensation risk.
* Logic checks for **Thermal Regulator power**; if the valve is unpowered (disabled), evacuation is triggered.