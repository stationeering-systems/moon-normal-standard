# (5) WATER PROBE - SYSTEMS OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors water supply

## FUNCTIONAL OVERVIEW
* Ensures minimal adequate water supply

## CONFIGURATION PARAMETERS
| Variable   | Description                     | Setting |
|------------|---------------------------------|---------|
| `MinWater` | Minimum required water supply L | `60`    |

## ALERT STATES
| Condition        | Alert         |
|------------------|---------------|
| Pipe Burst       | 35 (CRITICAL) |
| Low Water Supply | 25 (WARN)     |
