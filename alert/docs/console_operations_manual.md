# CONSOLE CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Cycles local status information on LED displays

## FUNCTIONAL OVERVIEW
* Displays the sector alert status from local Channel0
* Displays the local alert status from probes
* Displays the local entry status from Haven
* Displays fire and contaminant conditions from connected gas sensors

## HARDWARE INTERFACE
* **d0:** Haven

## CONFIGURATION PARAMETERS
| Variable         | Description                       | Setting            |
|------------------|-----------------------------------|--------------------|
| `HoldDuration`   | Pause duration between frames (s) | `2`                |
| `Probe`          | label                             | `"Probe"`          |
| `LocationStatus` | label                             | `"LocationStatus"` |

## NOTES
* Refer to [Reading Displays](https://stationeering.substack.com/i/182428013/reading-displays) for additional information