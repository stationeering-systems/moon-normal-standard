# SENTINEL-CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors gateways and returns the highest detected alert.

## FUNCTIONAL OVERVIEW
* Aggregates the max alert value from all gateways
* Monitors the health of the network as a whole

## HEALTH CHECKS
Health checks provide continuous validation of monitoring system integrity.

| Code   | Name               | Purpose                     |
|--------|--------------------|-----------------------------|
| 360000 | HealthcheckOffline | Checks for offline gateways |

## CONFIGURATION PARAMETERS
| Variable  | Description | Setting     |
|-----------|-------------|-------------|
| `Gateway` | label       | `"Gateway"` |

## NOTES
* HealthcheckOffline (360000) indicates degraded monitoring coverage when no higher-priority alerts are active. Critical Environment alerts (37) take precedence even when monitoring coverage is compromised, ensuring life-safety hazards remain visible.