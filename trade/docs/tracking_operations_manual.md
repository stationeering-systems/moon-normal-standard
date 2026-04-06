# TRACKING CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Locks onto a contact's position.

## FUNCTIONAL OVERVIEW
* Performs a full-sky scan to isolate the contact id
* Divides the scan region into nine proximity areas, using a timeout to narrow the search range.
* Locks the final position by sampling neighboring points and approximating horizontal and vertical coordinates
* Toggles the Setting register after the contact despawns.  This can be used to reset a stopwatch and track contact uptime for automated traffic systems.

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
| Large   | Medium | 3    | 250   | 8.5     | 120      |
| Exotic  | Medium | 4    | 100   | 8.5     | 1200     |

## CONFIGURATION PARAMETERS
| Variable               | Description                                          | Setting  |
|------------------------|------------------------------------------------------|----------|
| `TargetSignalStrength` | Maximum locked Signal Strength                       | `2`      |
| `AzimuthPeriod`        | Horizontal degrees traveled for full sky scan        | `1620`   |
| `ScanStepSize`         | Horizontal distance traveled per scan step           | `10`     |
| `ScanRatio`            | Scan detection power ratio                           | `0.2`    |
| `RefineRadius`         | Radial distance for refinement proximity detection   | `15.307` |
| `RefineAngle`          | Angular step size for refinement proximity detection | `45`     |

# MAINTENANCE & TROUBLESHOOTING

## Dish keeps checking the same positions in a loop

The refinement phase uses a flat-plane approximation to place nine search positions around the detection point.  Near the hemisphere boundary, spherical geometry causes the actual distance between the dish and the contact to be slightly larger than the calculation predicts.  If the contact falls outside the effective coverage of all nine positions, the dish cycles through them repeatedly without resolving.

**Observed behavior:**
* Dish moves to a position, pauses briefly, then advances to the next
* Movement traces a circular pattern around the initial detection point
* Contact is never acquired and the dish does not transition to lock
* Issue is most prominent for contacts detected at high elevations (V > 70°)

**Solution:** Increase the `Proximity Timeout Setting` in 0.5s increments until the contact transitions to the lock stage.  The timeout extends the dwell time at each position, compensating for the additional spherical distance.  Large and Exotic contacts are most susceptible due to their higher `WattsToResolve` value and have a higher suggested baseline timeout of 8.5s.