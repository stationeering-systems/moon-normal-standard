# TRACKING CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Locks onto a contact's position.

## FUNCTIONAL OVERVIEW
* Performs a full-sky scan to isolate the contact id
* Divides the scan region into nine proximity areas, using a timeout to narrow the search range.
* Locks the final position by sampling neighboring points and approximating horizontal and vertical coordinates

## HARDWARE INTERFACE
* **d0:** Dish
* **d1:** Contact Slot Index Setting
* **d2:** Minimum Watts Visible Setting
* **d3:** Proximity Timeout Setting
* **d4:** Downtime Setting

## CONTACT SETTINGS
| Contact | Dish   | Slot | Watts | Timeout | Downtime |
|---------|--------|------|-------|---------|----------|
| Utility | Small  | 0    | 0     | 0       | 300      |
| Basic   | Small  | 1    | 0     | 0       | 30       |
| Medium  | Small  | 2    | 20    | 4.5     | 30       |
| Large   | Medium | 3    | 250   | 8       | 120      |
| Exotic  | Medium | 4    | 100   | 8       | 1200     |

## CONFIGURATION PARAMETERS
| Variable               | Description                                          | Setting  |
|------------------------|------------------------------------------------------|----------|
| `TargetSignalStrength` | Maximum locked Signal Strength                       | `2`      |
| `AzimuthPeriod`        | Horizontal degrees traveled for full sky scan        | `1620`   |
| `ElevationRate`        | Vertical offset for every horizontal degree          | `0.0556` |
| `ScanStepSize`         | Horizontal distance traveled per scan step           | `10`     |
| `ScanRatio`            | Scan detection power ratio                           | `0.2`    |
| `RefineRadius`         | Radial distance for refinement proximity detection   | `15.307` |
| `RefineAngle`          | Angular step size for refinement proximity detection | `45`     |
