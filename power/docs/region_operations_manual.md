# REGION CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Monitors available charge and power usage and allocates power budgets to connected zones in priority order.

## FUNCTIONAL OVERVIEW
* Tracks the exponential moving average of actual power consumed within the region over the potential requested by zones
* Computes the available power budget to distribute to zones
* Distributes power budget across all available zones based priority and requested amount

## HARDWARE INTERFACE
* **d0..d5:** Zone Transformers (Mirrored)

## HARDWARE LABELING
Each connected transformer requires a matching logic reader with an identical label to retrieve the zone's requested potential.  The controller uses these paired labels to distribute available power budget to zones.

**Example:**
* Transformer (Logic Mirror) labeled `A-1.0`
* Requested Potential (Logic Reader) labeled `A-1.0`

## CONFIGURATION PARAMETERS
| Variable | Description                   | Setting |
|----------|-------------------------------|---------|
| `Period` | Generation offline period (s) | `600`   |
| `Alpha`  | EMA learning rate (ticks)     | `3600`  |

## MAINTENANCE & TROUBLESHOOTING

### Zone is not receiving adequate power

1.1 Is the region controller setting > 1?
* IF NO - Load shedding, system normal
* IF YES - Verify system settings and connections