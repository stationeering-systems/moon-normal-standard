# ZONE CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Calculates the requested allocation of characterized and uncharacterized loads and distributes power to subnetworks in priority order.

## FUNCTIONAL OVERVIEW
* Calculates the total requested potential of power for a zone.
* Turns subnetworks on and off based on available power budget

## HARDWARE INTERFACE
* **d0..d5:** Subnetwork Transformers

## CONFIGURATION PARAMETERS
| Variable    | Description                     | Setting |
|-------------|---------------------------------|---------|
| `BasePower` | Zone transformer base power (W) | `10`    |

## MAINTENANCE & TROUBLESHOOTING

### Subnetwork is offline

**STEP 1: Check Power**

1.1 Is the subnetwork ON?
* IF NO - Continue to STEP 1.2
* IF YES - Verify system settings and connections

1.2 Is zone potential >= zone requested?
* IF NO - Refer to [Region System Operations Manual](region_operations_manual.md)
* IF YES - Check that the subnetwork is registered to the zone